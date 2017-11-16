# UIView详解


## 概述

视图是应用程序中用户界面的基本组成部分，`UIView`类定义了所有视图的通用行为。视图对象在其边界矩形内呈现内容，并处理与该内容有关的任何交互。`UIView`类是一个具体类，可以使用其实例对象来显示一个固定的背景颜色，也可以子类化`UIView`来绘制更复杂的内容。要展示应用程序中常见的标签、图像、 按钮 和其它界面元素，应首先选择使用UIKit框架提供的视图子类。

视图对象是应用程序与用户交互的主要方式，其主要职责有：

- 绘制图形和执行动画
    - 使用UIKit框架或者Core Graphics框架在视图的矩形区域中绘制内容。
    - 视图的一些属性值可以用来执行动画。
- 布局和管理子视图
    - 视图可能包含多个子视图。
    - 视图可以调整子视图的大小和位置。
    - 使用Auto Layout定义调整视图大小和重新定位视图的规则，并以此规则来响应视图层的更改。
- 事件处理
    - 视图对象是`UIResponder`类的子类对象，能够响应触摸事件和其它类型的事件。
    - 视图可以附加手势识别器来处理常见的手势。
    
视图可以被嵌套在其它视图内构成视图层，这样能够方便我们组织展示相关内容。嵌套视图时会在子视图和父视图之间创建一种父子关系。父视图可以包含任意数量的子视图，但子视图只能有一个父视图。默认情况下，当子视图的可见区域超出其父视图的矩形区域时，不会对子视图内容作裁剪，但可以设置父视图对象的`clipsToBounds`属性值来更改默认行为。

每个视图的几何图形由其`frame`和`bounds`属性决定，`frame`属性决定了视图在其父视图坐标系中的原点和尺寸，`bounds`属性决定了视图的内部尺寸。还可以通过更改视图对象的`center`属性来重新定位视图而不用直接修改其`frame`和`bounds`属性。

## 基础

### 创建并配置视图对象

创建视图最简单的方式是使用**Interface Builder**直接将视图添加到界面上，代码创建视图的默认方式是调用视图的`initWithFrame`方法，此方法会设置好视图相对于父视图的初始大小和位置。


有关视图控制器如何加载和管理其关联的nib文件的信息可以参看[View Controller Programming Guide for iOS](https://developer.apple.com/library/content/featuredarticles/ViewControllerPGforiPhoneOS/index.html#//apple_ref/doc/uid/TP40007457)，有关从xib文件中以编程方式加载视图的信息可以参看[Nib Files](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/LoadingResources/CocoaNibs/CocoaNibs.html#//apple_ref/doc/uid/10000051i-CH4)。

