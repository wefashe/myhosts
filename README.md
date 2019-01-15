# 打造自己的hosts同步在线更新管理: Github+SwitchHosts！

## 需要的工具
1. 注册[Github](https://github.com)点我注册
2. 下载解压[SwitchHosts！点我下载](http://oldj.github.io/SwitchHosts/#cn)

## 教程

1. 注册Github我就不说了，注册完毕之后，点击右上角新建项目，

![1](https://upload-images.jianshu.io/upload_images/7734354-706c864176ae0eab.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

2. 填写相关信息之后完成创建，除了名称是必填其他都是选填，我勾选创建readme，

![2-1](https://upload-images.jianshu.io/upload_images/7734354-6b7ccaac62664afa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)
![2-2](https://upload-images.jianshu.io/upload_images/7734354-87efa3f190e6404f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

3. 接下来我们就要开始创建Hosts了，我们首先点击上图的create new file，然后首先我们为该hosts命名，然后下面就是大大的代码编辑窗口，对于hosts来说代码很简单，左侧ip地址，空一格，然后是域名。

![3](https://upload-images.jianshu.io/upload_images/7734354-9288c3c1e09da62e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

4. 填写完毕之后，在下方点击原谅色的保存

![4](https://upload-images.jianshu.io/upload_images/7734354-a89d5253e0b1b714.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

5. 下面就需要获取能直接在线更新的地址，首先我们点开刚才创建的文件，在地址栏上方有网页地址，可是这个地址我们软件可无法识别

![5-1](https://upload-images.jianshu.io/upload_images/7734354-dac9f6297bf7c32a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

点击RAW转换为在线更新地址，下面的地址我们可以试着用浏览器打开，你会发现就是一个可以直接下载的文本文件，这就是我们需要填入软件中的更新地址

![5-2](https://upload-images.jianshu.io/upload_images/7734354-330214500c07442c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

**PC端（Win/Mac/Linux 通用）**

7. 打开SwitchHosts！点击左下角添加远程hosts，添加下面的地址确定添加

![7-1](https://upload-images.jianshu.io/upload_images/7734354-f0104915878bc252.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

然后点击小勾勾，再点击后面那个绿色的小点点，绿色的就表示启用了。像这样：

![7-2](https://upload-images.jianshu.io/upload_images/7734354-c74b10fb87134339.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

## SwitchHosts不能及时生效的解决方案
>SwitchHosts是一个管理、切换多个 hosts 方案的工具。 它是一个免费开源软件。平时我们在开发的时候，到了自测这一步，都要将代码放到测试机上。这时候就可以将网站的资源位置转到测试机的IP上去，从而可以在互联网访问正常的网站的时候，加载自己测试机上的资源。

### 1. 问题
我们在开启SwitchHosts相应的IP转换的时候： 
（1）浏览器上要改变的内容并没有生效； 
（2）或者有时候我们关闭了IP转换的时候，浏览器上要改变的内容却还在生效； 
（3）有时候过了一段时间这一切又恢复正常了。

### 2. 根源
这一切的根源是源自浏览器和电脑留下来的缓存。因为缓存问题，浏览器只是读取缓存，所以导致真正需要的请求发出去并没有请求到自己想要的资源。有的人说已经清理缓存了，但是你并没有清理得完整，真正需要清理的缓存还要涉及到DNS上的缓存和电脑host上的缓存。

### 3. 方案
  1. DNS的查看
  ```
  # windows
  ipconfig/displaydns

  # chrome浏览器
  chrome://net-internals/#dns
  ```

  2. DNS的清理 
  ```  
  # windows->运行 -> 输入cmd -> 在CMD窗口输入
  ipconfig /flushdns
  
  #Linux终端输入
  sudo rcnscd restart
  
  #对于systemd发行版，请使用命令
  sudo systemctl restart NetworkManager
  
  #Mac OS X终端输入
  sudo killall -HUP mDNSResponder
  
  #Android开启飞行模式 -> 关闭飞行模式
  #通用方法拔网线(断网) -> 插网线(重新连接网络)
  ```
  如果要清理chrome浏览器的话： 
  
  ![chrome](https://img-blog.csdn.net/20180517115722890?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM3OTQzMjk1/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
  
### 4. 提示
如果是用chrome浏览器开发的话，可以先考虑清理浏览器的DNS缓存即可。如果实在还是出现了问题的话，再进一步清理系统的的DNS缓存。


## 修改更新

此时我们编辑hosts还不是很方便，干脆新建一个快捷方式，直接指向编辑页面。

这个hosts列表所有支持远程hosts的软件都以用，手机，路由器，服务器都可以，而且不怕丢失，如果需要修改条目，登陆GitHub点击修改保存，然后软件界面点击更新，好了！

![123](https://upload-images.jianshu.io/upload_images/7734354-07ef6f38448bd500.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp)

## 最后
本方案应该是hosts管理最便捷和安全的方案了，不在本地操作hosts还可以有效防止病毒和恶意软件更改hosts，即便被更改了我们刷新一下就ok了，不会影响上网，非常便于维护操作，我们把常用网站导入hosts可以让上网更流畅，细水长流，每天加几条就可以了，毕竟每个人上的网站其实并不多，所以我并不建议直接用网上其他人的hosts，无用信息太多了。
