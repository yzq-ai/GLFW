# GLFW

[![项目构建状态](https://travis-ci.org/glfw/glfw.svg?branch=master)](https://travis-ci.org/glfw/glfw)
[![项目构建状态](https://ci.appveyor.com/api/projects/status/0kf0ct9831i5l6sp/branch/master?svg=true)](https://ci.appveyor.com/project/elmindreda/glfw)
[![Coverity Scan](https://scan.coverity.com/projects/4884/badge.svg)](https://scan.coverity.com/projects/glfw-glfw)

## 介绍

GLFW是一个开源、跨平台的库，用于OpenGL、OpenGL ES和Vulkan应用程序的开发。它提供了一个简单、独立于平台的API，用于创建窗口、上下文、表面、读取输入、处理事件等。

GLFW原生支持Windows、macOS和Linux以及其他类Unix系统。Wayl和协议的实验性实现可用，但还没有正式支持。

GLFW基于[zlib/libpng](http://www.glfw.org/license.html)许可证发布。

最新的稳定版本是3.2.1版。


请查看[下载页面](http://www.glfw.org/download.html)获取详细信息和文件，或获取指向最新的稳定版本的`latest`分支。从3.0开始，每个发布版本都有相应的[注释](https://github.com/glfw/glfw/releases)标记，包括源代码和二进制归档文件。版本[历史记录](http://www.glfw.org/changelog.html)列出了每个发布版本中所有用户可见的更改。


这是版本3.3的开发分支，目前_尚未描述_。预发布文档可在[此处](http://www.glfw.org/docs/3.3/)获得。

`master`分支是稳定的集成分支，并_应该_始终能够在所有支持的平台上编译和运行，尽管新添加功能的细节可能会发生变化，直到它们被包含在一个发布中。新的功能和许多bug修复都存在于[其他分支](https://github.com/glfw/glfw/branches/all)中，直到它们足够稳定才能合并。

如果您是GLFW的新手，可以在这里找到GLFW 3的[教程](http://www.glfw.org/docs/latest/quick.html)。如果您以前使用过GLFW 2，有一个[过渡指南](http://www.glfw.org/docs/latest/moving.html)来移植到GLFW 3 API。


## 编译GLFW
GLFW本身仅需要您的窗口系统的头文件和库。它不需要任何上下文创建API（WGL，GLX，EGL，NSGL，OSMesa）或渲染API（OpenGL，OpenGL ES，Vulkan）的头文件来启用对它们的支持。

GLFW支持在Windows上使用Visual C++ 2010及更高版本，MinGW和MinGW-w64，使用Clang在macOS上，使用GCC和Clang在Linux和其他类Unix系统上进行编译。它也可能会编译到其他环境中，但这种情况通常没有经过测试。

所有受支持编译器都可下载预编译的[Windows二进制](http://www.glfw.org/download.html)。

有关如何自行编译GLFW的更多信息，请参见[编译指南](http://www.glfw.org/docs/latest/compile.html)。


## 使用GLFW

请参见[文档](http://www.glfw.org/docs/latest/)，了解教程，指南和API参考。



## 对GLFW的贡献

有关更多信息，请参见[贡献指南](https://github.com/glfw/glfw/blob/master/docs/CONTRIBUTING.md)。



## 系统要求

GLFW支持Windows XP及更高版本以及macOS 10.7及更高版本。Linux和其他运行X Window System的类Unix系统即使没有桌面环境或现代扩展也是支持的，尽管某些功能需要运行窗口或剪贴板管理器。OSMesa后端需要Mesa 6.3。

有关更多信息，请参见文档中的[兼容性指南](http://www.glfw.org/docs/latest/compat.html)。

## 依赖关系


GLFW本身仅依赖于你的窗口系统的头文件和库。

（实验性的）Wayl和后端还依赖于`extra-cmake-modules`s包，用于生成Wayl和协议头文件。

示例程序和测试程序依赖于一些小型库。这些库位于`deps/`目录中：


 - [getopt\_port](https://github.com/kimgr/getopt_port/) 用于带命令行选项的示例程序
 - [TinyCThread](https://github.com/tinycthread/tinycthread) 用于多线程示例程序
 - [glad](https://github.com/Dav1dde/glad) 用于现代OpenGL的示例程序的OpenGL 3.2核心加载器生成
 - [linmath.h](https://github.com/datenwolf/linmath.h)用于示例程序中的线性代数
 - [Nuklear](https://github.com/vurtun/nuklear) 用于测试和示例程序的用户界面
 - [stb\_image\_write](https://github.com/nothings/stb) 用于将图像写入磁盘
 - [Vulkan headers](https://www.khronos.org/registry/vulkan/) 用于Vulkan测试


Vulkan示例还需要安装LunarG Vulkan SDK，否则它将不会被包含在构建中。在macOS上，你需要手动提供SDK的路径，因为它没有标准安装位置。

如果CMake能找到Doxygen工具，文档将使用[Doxygen](http://doxygen.org/) 生成。



## Reporting bugs

发现的漏洞请报告到我们的[issue跟踪器](https://github.com/glfw/glfw/issues)。请查看[贡献指南](https://github.com/glfw/glfw/blob/master/docs/CONTRIBUTING.md)，以获取提交漏洞报告时应包含的信息。


## 更改日志

- 新增 `glfwGetError` 函数 用于查询最后一个错误代码及其描述 (#970)
- 新增 `glfwUpdateGamepadMappings` 函数 用于导入 SDL_GameControllerDB 格式的游戏手柄映射 (#900)
- 新增 `glfwJoystickIsGamepad` 函数 用于查询一个游戏手柄是否有映射 (#900)
- 新增 `glfwGetJoystickGUID` 函数 用于查询一个游戏手柄的 SDL 兼容 GUID (#900)
- 新增 `glfwGetGamepadName` 函数 用于查询游戏手柄映射提供的名称 (#900)
- 新增 `glfwGetGamepadState` 函数, `GLFW_GAMEPAD_*` 和 `GLFWgamepadstate` 用于检索游戏手柄输入状态 (#900)
- 新增 `glfwGetWindowContentScale`, `glfwGetMonitorContentScale` 和
  `glfwSetWindowContentScaleCallback` 以支持 DPI 感知渲染 (#235、#439、#677、#845、#898)
- 新增 `glfwRequestWindowAttention` 函数 用于请求用户关注 (#732、#988)
- 新增 `glfwGetKeyScancode` 函数 t允许检索键盘的平台相关扫描码 (#830)
- 新增 `glfwSetWindowMaximizeCallback` 和 `GLFWwindowmaximizefun` 用于接收窗口最大化事件 (#778)
- 新增 `glfwSetWindowAttrib` 函数 用于更改窗口属性 (#537)
- 新增 `glfwGetJoystickHats` 函数 用于查询游戏手柄的键帽 (#889、#906、#934)
- 新增 `glfwInitHint`函数  用于设置初始化提示
- 新增 `glfwWindowHintString` 用于设置字符串类型的窗口提示 (#893、#1139)
- 新增 `glfwGetWindowOpacity` 和 `glfwSetWindowOpacity` 用于控制整个窗口的透明度 (#1089)
- 新增 `glfwSetMonitorUserPointer` 和 `glfwGetMonitorUserPointer` 用于每个监视器的用户指针
- 新增 `glfwSetJoystickUserPointer` 和 `glfwGetJoystickUserPointer` 用于每个游戏手柄的用户指针
- 新增 `glfwGetX11SelectionString` 和 `glfwSetX11SelectionString`函数 用于访问 X11 主选择 (#894、#1056)
- 新增 无头文件[OSMesa](http://mesa3d.org/osmesa.html) 的 后端 (#850) 
- 新增 定义于`GLAPIENTRY` 公共头文件
- 新增 `GLFW_TRANSPARENT_FRAMEBUFFER` 窗口提示和属性，用于控制每个像素缓冲区的透明度 (#197、#663、#715、#723、#1078)
- 新增 `GLFW_HOVERED`  窗口属性，用于轮询光标悬停状态 (#1166)
- 新增 `GLFW_CENTER_CURSOR`  窗口提示，用于控制光标居中 (#749、#842)
- 新增 `GLFW_FOCUS_ON_SHOW` 窗口提示和属性，用于控制调用 show window 时的输入焦点 (#1189)
- 新增 `GLFW_SCALE_TO_MONITOR` 窗口提示，用于自动调整窗口大小 (#676、#1115)


- 新增 `GLFW_JOYSTICK_HAT_BUTTONS` 初始化提示 (#889)
- 新增 `GLFW_LOCK_KEY_MODS`  输入模式和 `GLFW_MOD_*_LOCK` 模式位 (#946)
- 新增macOS 特定的 `GLFW_COCOA_RETINA_FRAMEBUFFER` 窗口提示
- 新增macOS 特定的 `GLFW_COCOA_FRAME_NAME` 窗口提示 (#195)
- 新增macOS 特定的 `GLFW_COCOA_GRAPHICS_SWITCHING` 窗口提示 (#377,#935)
- 新增macOS 特定的 `GLFW_COCOA_CHDIR_RESOURCES` 初始化提示
- 新增macOS 特定的 `GLFW_COCOA_MENUBAR` 初始化提示
- 新增 X11 specific `GLFW_X11_CLASS_NAME` 和 `GLFW_X11_INSTANCE_NAME` 窗口提示 (#893,#1139)
- 新增 `GLFW_INCLUDE_ES32` 用于包括OpenGL ES 3.2头文件
- 新增 `GLFW_OSMESA_CONTEXT_API` 用于使用 OSMesa 创建[OpenGL上下文](https://www.mesa3d.org/osmesa.html) (#281)
- 新增 `GenerateMappings.cmake`  脚本，用于更新游戏手柄映射
- 当窗口有上下文时，将使 `glfwCreateWindowSurface` 发出错误 (#1194、#1205)
- 弃用 clipboard 字符串函数的窗口参数
- 弃用 charmods 回调
- 删除 `GLFW_USE_RETINA` 编译时选项
- 删除 `GLFW_USE_CHDIR` 编译时选项
- 删除 `GLFW_USE_MENUBAR` 编译时选项
- bug修复: 在全屏窗口上调用 `glfwMaximizeWindow` 时未被忽略
- bug修复: `GLFW_INCLUDE_VULKAN` 不能与相应的OpenGL和OpenGL ES头文件宏组合使用
- bug修复: 当 `_GLFW_VULKAN_STATIC `被启用时，`glfwGetInstanceProcAddress `对 `vkGetInstanceProcAddr `返回 `NULL`
- bug修复: 测试和示例CMake文件中使用无效的库路径 (#930)
- bug修复: 合成释放事件的扫描码始终为零
- bug修复: 生成的 Doxyfile 不处理带有空格的路径 (#1081)
- [Win32] 新增系统错误字符串到相关的GLFW错误描述 (#733)
- [Win32] 将禁用游标模式运动输入移动到 `WM_INPUT `(#125)
- [Win32]  从游戏手柄轴数据中移除XInput循环死区 (#1045)
- [Win32] bug修复: 用户无法将未装饰的窗口最小化 (#861)
- [Win32] bug修复: 某些控制器下 Deadzone 逻辑可能会下溢 (#910)
- [Win32] bug修复: `FindVulkan.cmake `中的位数测试是 VS 特定的 (#928)
- [Win32] bug修复: 在具有加载程序但没有ICD的系统上，`glfwVulkanSupported` 会发出错误 (#916)
- [Win32] bug修复: 未将非图标化全屏窗口用于防止屏幕变黑或启用密码的屏幕保护（#851）
- [Win32] bug修复: 鼠标捕获逻辑丢失了次要释放消息（＃954）
- [Win32] bug修复: 未搜索32位Vulkan加载器库静态文件（#956）
- [Win32] bug修复: 自SDK 1.0.42.0起，Vulkan库具有新路径（＃956）
- [Win32] bug修复: 未列举没有显示设备的监视器（＃960）
- [Win32] bug修复: 未发出监视器事件（#784）
- [Win32] bug修复: Cygwin DLL安装到了错误的目录中（＃1035）
- [Win32] bug修复: 通过XInput规范化轴数据不正确（#1045）
- [Win32] bug修复: `glfw3native.h`取消定义外部的`APIENTRY`（＃1062）
- [Win32] bug修复: 禁用光标模式会导致标题按钮无法使用（＃650，＃1071）
- [Win32] bug修复: 返回的键名与其他平台不匹配（＃943）
- [Win32] bug修复: 无装饰窗口无法最大化到工作区域（＃899）
- [Win32] bug修复: 在进入全屏模式时，窗口会被调整大小两次（＃1085）
- [Win32] bug修复: HID设备通知没有取消注册（＃1170）
- [Win32] bug修复:即使将`GLFW_FOCUSED命`中设置为false也会激活`glfwCreateWindow`窗口（＃1179，＃1180）
- [Win32] bug修复: 键盘等于键被报告为`GLFW_KEY_UNKNOWN`（＃1315，＃1316）
- [X11] 将光标模式动态输入移动到XI2的`XI_RawMotion`(#125)
- [X11] 用动态加载替换了`_GLFW_HAS_XF86VM`的编译时选项
- 
- [X11] bug修复: `glfwGetVideoMode`在Cygwin/X上会导致段错误
- [X11] bug修复: 动态X11库加载未使用完整sonames（＃941）
- [X11] bug修复: 64位上的窗口创建会读取栈顶部的数据（＃951）
- [X11] bug修复: XDND支持存在多个不符合规范的问题（＃968）
- [X11] bug修复: 已禁用R和R监视器路径，尽管R和R正常工作（＃972）
- [X11] bug修复: 具有低轮询速度的IM重复键事件将泄漏（＃747）
- [X11] bug修复: 通过R和R设置伽玛坡道没有验证斜坡尺寸
- [X11] bug修复: 键名字符串编码取决于当前语言环境（＃981，＃983）
- [X11] bug修复: 不支持增量读取选择（＃275）
- [X11] bug修复: 选择IO报告但不支持`COMPOUND_TEXT`
- [X11] bug修复: 从选择中读取的Latin-1文本未转换为UTF-8
- [X11] bug修复: 在关闭显示器之前卸载NVidia EGL可能会导致段错误
- [X11] bug修复: 检查窗口最大化时属性可能会崩溃一些WM（＃1356）
- [X11] bug修复: 在进入事件上更新光标位置（＃1366）
- [Linux] 新增解决方案，用于在2.6.39之前的内核头文件中缺少`SYN_DROPPED`（＃1196）
- [Linux] 使用evdev进行手柄输入（＃906，＃1005）
- [Linux] bug修复: 事件处理未检测到手柄断开连接（＃932）
- [Linux] bug修复: 手柄设备路径可能会被截断（＃1025）
- [Linux] bug修复: 如果inotify创建失败，则 `glfwInit`将失败（＃833）
- [Linux] bug修复: 未使用任何必需的特征宏即使用了`strdup`（＃1055）
- [Cocoa] 新 MoltenVK通过[MoltenVK](https://moltengl.com/moltenvk/)支持创建Vulkan窗口表面 (#870)
- [Cocoa] 新增当可用时加载`MainMenu.nib`的支持
- [Cocoa] bug修复: 禁用窗口纵横比会导致断言（＃852）
- [Cocoa] bug修复: 窗口创建未设置第一响应者（＃876，＃883）
- [Cocoa] bug修复: 删除使用过时的`CGDisplayIOServicePort`函数的方法（＃165，＃192，＃508，＃511）


- [Cocoa] bug修复: 在macOS 10.12及以上的系统中已禁用使用过时的`CGDisplayModeCopyPixelEncoding`函数
- [Cocoa] bug修复: 在App Sandbox中运行会发出警告（＃816，＃882）
- [Cocoa] bug修复: 第一次创建窗口之后创建的窗口未进行级联（＃195）
- [Cocoa] bug修复: 使用`glfwSetWindowMonitor`离开视频模式可能会设置错误的位置和大小（＃748）
- [Cocoa] bug修复: 图标化全屏窗口无法恢复（＃848）
- [Cocoa] bug修复: 对于某些视频模式，全屏帧缓冲区大小不正确（＃682）
- [Cocoa] bug修复: 手柄键帽和按钮的值范围被忽略（＃888）
- [Cocoa] bug修复: IME的字符串对象更新方式不符合惯例（＃1050）
- [Cocoa] bug修复: 当显示用户通知时，隐藏或禁用的光标将变为可见（＃971，＃1028）
- [Cocoa] bug修复: 由于按住并保持，一些字符不会重复（＃1010）
- [Cocoa] bug修复: 全屏或无装饰窗口时窗口标题丢失（＃1082）
- [Cocoa] bug修复: 进入全屏时窗口大小调整了两次（＃1085）
- [Cocoa] bug修复: 重复的大小事件没有被过滤（＃1085）
- [Cocoa] bug修复: 如果必要，事件轮询不会初始化AppKit（＃1218）
- [Cocoa] bug修复: 在10.14上，OpenGL渲染最初不可见（＃1334，＃1346）
- [WGL] 新增`WGL_EXT_colorspace` 用于支持OpenGL ES contexts
- [WGL] 新增`WGL_ARB_create_context_no_error` 支持
- [GLX] 新增`GLX_ARB_create_context_no_error`支持
- [GLX] bug修复: 如果没有GLXFBConfigs可用，则创建上下文可能会导致段错误（＃1040）
- [EGL] 新增 `EGL_KHR_get_all_proc_addresses`支持 (#871)
- [EGL] 新增 `EGL_KHR_context_flush_control`支持
- [EGL] bug修复: 对`EGL_RGB_BUFFER`的测试无效


## 联系方式

在[glfw.org](http://www.glfw.org/) 网站上，您可以找到GLFW的最新版本、新闻、文档以及其他相关信息。

如果您在使用GLFW过程中有任何问题，请参与我们的[论坛](http://discourse.glfw.org/)或者在Freenode上的`#glfwIRC`[频道](http://freenode.net/)提问。

如果您遇到了bug，或者想提交一个补丁或者提出新的功能请求，请在GitHub上的[issue tracker](https://github.com/glfw/glfw/issues)中进行提交。

最后，如果您有兴趣参与GLFW的开发或将其移植到您喜欢的平台上，请加入我们的论坛、GitHub或IRC。


## Acknowledgements

感谢全球的人们奉献自己时间和贡献他们的能力来创造GLFW。

 - Bobyshev Alex和er
 - Matt Arsenault
 - David Avedissian
 - Keith Bauer
 - John Bartholomew
 - Coşku Baş
 - Niklas Behrens
 - Niklas Bergström
 - Denis Bernard
 - Doug Binks
 - blanco
 - Kyle Brenneman
 - Rok Breulj
 - Martin Capitanio
 - David Carlier
 - Arturo Castro
 - Chi-kwan Chan
 - Ian Clarkson
 - Michał Cichoń
 - Lambert Clara
 - Yaron Cohen-Tal
 - Omar Cornut
 - 和rew Corrigan
 - Bailey Cosier
 - Noel Cower
 - Jason Daly
 - Jarrod Davis
 - Olivier Delannoy
 - Paul R. Deppe
 - Michael Dickens
 - Роман Донченко
 - Mario Dorn
 - Wolfgang Draxinger
 - Jonathan Dummer
 - Ralph Eastwood
 - Fredrik Ehnbom
 - Robin Eklind
 - Siavash Eliasi
 - Felipe Ferreira
 - Michael Fogleman
 - Gerald Franz
 - Mário Freitas
 - GeO4d
 - Marcus Geelnard
 - Stephen Gowen
 - Kovid Goyal
 - Eloi Marín Gratacós
 - Stefan Gustavson
 - Jonathan Hale
 - Sylvain Hellegouarch
 - Matthew Henry
 - heromyth
 - Lucas Hinderberger
 - Paul Holden
 - Warren Hu
 - IntellectualKitty
 - Aaron Jacobs
 - Erik S. V. Jansson
 - Toni Jovanoski
 - Arseny Kapoulkine
 - Cem Karan
 - Osman Keskin
 - Josh Kilmer
 - Cameron King
 - Peter Knut
 - Christoph Kubisch
 - Yuri Kunde Schlesner
 - Konstantin Käfer
 - Eric Larson
 - Robin Leffmann
 - Glenn Lewis
 - Shane Liesegang
 - Eyal Lotem
 - Tristam MacDonald
 - Hans Mackowiak
 - Дмитри Малышев
 - Zbigniew M和ziejewicz
 - Célestin Marot
 - Kyle McDonald
 - David Medlock
 - Bryce Mehring
 - Jonathan Mercier
 - Marcel Metz
 - Liam Middlebrook
 - Jonathan Miller
 - Kenneth Miller
 - Bruce Mitchener
 - Jack Moffitt
 - Jeff Molofee
 - Pierre Morel
 - Jon Morton
 - Pierre Moulon
 - Martins Mozeiko
 - Julian Møller
 - ndogxj
 - Kristian Nielsen
 - Kamil Nowakowski
 - Denis Ovod
 - Ozzy
 - 和ri Pálsson
 - Peoro
 - Braden Pellett
 - Christopher Pelloux
 - Arturo J. Pérez
 - Anthony Pesch
 - Orson Peters
 - Emmanuel Gil Peyrot
 - Cyril Pichard
 - Keith Pitt
 - Stanislav Podgorskiy
 - Alex和re Pretyman
 - przemekmirek
 - Philip Rideout
 - Eddie Ringle
 - Jorge Rodriguez
 - Ed Ropple
 - Aleksey Rybalkin
 - Riku Salminen
 - Br和on Schaefer
 - Sebastian Schuberth
 - Christian Sdunek
 - Matt Sealey
 - Steve Sexton
 - Arkady Shapkin
 - Yoshiki Shibukawa
 - Dmitri Shuralyov
 - Daniel Skorupski
 - Bradley Smith
 - Patrick Snape
 - Erlend Sogge Heggen
 - Julian Squires
 - Johannes Stein
 - Pontus Stenetorp
 - Michael Stocker
 - Justin Stoecker
 - Elviss Strazdins
 - Paul Sultana
 - Nathan Sweet
 - TTK-B和it
 - Sergey Tikhomirov
 - Arthur Tombs
 - Ioannis Tsakpinis
 - Samuli Tuomola
 - Matthew Turner
 - urraka
 - Elias V和erstuyft
 - Stef Velzel
 - Jari Vetoniemi
 - Ricardo Vieira
 - Nicholas Vitovitch
 - Simon Voordouw
 - Corentin Wallez
 - Torsten Walluhn
 - Patrick Walton
 - Xo Wang
 - Jay Weisskopf
 - Frank Wille
 - Ryogo Yoshimura
 - 和rey Zholos
 - Santi Zupancic
 - Jonas Ådahl
 - Lasse Öörni
 - 感谢GLFW社区中所有未被提及和匿名的贡献者，他们为我们提供了bug报告、补丁、反馈、测试和鼓励。



