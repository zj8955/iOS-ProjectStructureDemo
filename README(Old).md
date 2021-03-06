# iOS-ProjectStructureDemo

仅以此，记录下当前想到的比较顺眼项目构架

```
    ├── <Router>                 负责APP层面业务的模块
    ├── <CodeFeed>               项目真正的构建内容
    ├── <PrefixHeader>           预编译文件
    ├── <Utils>                  适用于本项目的自定义类库。根据功能可以细分下去。
    ├── <Supporting Files>       系统配置文件及组成基础构架的文件
    └── <Pods（或Carthage）>工程  第三方SDK以及自己做的小工具
```

# Router ——负责APP层面业务的模块

处理APP层面的业务，其下分为

```
    ├── <M>  模型
    └── <VM> 模块间的业务处理
```

其中

`M`层存放和App相关的模型信息

`VM`层负责App层面业务，

# CodeFeed ——存放APP页面实际构建的代码

其内部分

```
    ├── <SuperCode>         模块中所用到的通用的父视图的集合（尽可能的少）
    ├── <EntityCode>        项代码实体，包含所有的页面的构建
    └── <PublicCode>        在多个页面用到的公共的页面（控制器）
```

其中`<EntityCode>`和`<PublicCode>`

内部以`MVVM`构架进行搭建，其下分为

```
    ├── <M>  模型
    ├── <V>  视图
    └── <VM> 视图模型的业务处理
```

其中

`M`层存放模型信息

`V`层存放模块相关的控制器和视图

`VM`层数据请求，数据处理，业务逻辑，包含为显示做的准备工作的相关视图（tableView、collectionView代理）逻辑。

依据`VIPER`的，在VM层内部将其业务剥离为：

`Interactor`：处理业务逻辑。

`Presenter` ：为显示（从交互器接受的内容）做的准备工作的相关视图逻辑。

`Entity` ：包含交互器要使用的基本模型对象。

# PrefixHeader

存放`.pch`文件及其它进行预编译的文件

例如：只重写了 `+ (void)load`的类。

# Utils

存放只适用于当前项目的类（可以通用的类，应该提取出去，放在托管平台进行维护）

根据功能可以细分下去。UI类，Data类...等

# Supporting Files

存放APP的配置文件 `info.plist`、`InfoPlist.strings`、`main.m`、`Appdelegate`等

窗口的根控制器

# Pods（或Carthage）

存放第三方工具及自己托管于第三方平台的工具


