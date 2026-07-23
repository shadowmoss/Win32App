#### Win32编程环境搭建。
1. Windows32编程需要使用,Windows SDK KIT下载网址
2. Windows SDK Kit提供了，win32编程所需要的header、library、compile、linker。
3. Windows SDK支持开发32bit-64bit的应用。
4. 下载地址:[download](https://learn.microsoft.com/en-us/windows/apps/windows-sdk/)
#### windows编程协定
1. win32代码库，包含了大量的函数、和Component Object Model(COM)接口。只有很少的Windows APIs提供了C++ classes(除了GDI+,一个2-D图形APIS)
2. win32头文件中包含了大量的typedef 大部分都定义在windef.h中。
3. win32中的Bool类型是int的别名，与C++的bool类型区分开来。windef.h中也定义了用于Bool类型的两个值。
4. 指令类型，Win32定了许多数据类型用于指向某个类型。通常情况下拥有前缀P-或者LP-在名称当中。
5. 大量的win32命名使用了Hungarian notation表示法。
#### 使用string时的一些注意事项
1. 最好在源代码开头定义#define UNICODE表示使用的是UNICODE编码的字符串、字符、方便后续对应用进行国际化。
2. Win32中的很多函数有使用了Unicode和ANSI的两个版本。浏览win32 API时需注意。
#### 什么是window
1. 屏幕和Window坐标，win32的坐标永远将窗口左上角视为(0,0)
#### 应用程序的入口
1. `wWinMain`和`WinMain`函数是Windows APP的主要入口程序。`wWinMain`和`WinMain`的主要区别在于pCmdLine使用的字符编码`wWinMain`和`WinMain`一个使用Unicode字符编码一个使用ASNI字符编码。  其余参数如第一个参数都是当前窗口的句柄（handle）
2. handle是Windows系统用于管理系统所创建的Window的一个值，他不是当前Window的指针，他只是一个值。用于传递给Win32 API 对窗口进行操作的值。
#### 使用Windows Win32 代码库开发的一些惯例
1. 因为Windows Win32头文件很多时候关联到多个库。有些使用的内容是直接定义在头文件的，宏Macro,结构体，直接包含头文件可以解决问题，还有一些是库函数，这些必须指定需要链接的库，需要的链接库去到Microsoft Learn网站进行查询，拉到库函数页面的最后去查看需要链接的库。