   生活在世界上最大的局域网中，想必很多人都对墙外的世界充满兴趣。而GFW的存在则阻断了大部分人通向墙外的道路，虽然其中很多人使用某门，某灯等实现了翻墙看世界的目的，但是很多免费软件既有流量限制，又会限制网速，而且还经常失灵。因此，搭建一个属于自己的VPN就势在必行了。

  搭建一个VPN首先需要一个国外的服务器。现在比较出名的VPS提供商有linode、vultr、DigitalOcean、搬瓦工等。各位可以按照自己的需要挑选，当然这些服务商都不是免费的，目前最低的服务是$5/月。不过既然是收费的服务商，各位也不用担心收了钱就跑路，这几家都是比较有名比较有信誉的服务商，不但不会只收钱不办事，如果你有任何疑问还可以直接发信息提问，他们的工程师都会很快答复的。按照笔者自己的经验，基本在半个小时之内就会很仔细的答复你。PS：现在这几家服务商都会对新注册用户提供一定的优惠，各位可以在某度搜索他们的优惠码，像linode就为新注册的用户赠送了$20，而DigitalOcean则免费两个月。

#     注册VPS

    在购买VPS之前，需要一张信用卡。银联VISA都可以，因为这几家服务商基本都不支持支付宝，所以我们需要在paypal上注册一个账户，并绑定信用卡用来支付。在此附上paypal的官方网站：[paypal](https://www.paypal.com/c2/webapps/mpp/sem/brandv5?dclid=CMG9hdjSxtoCFVANKgodCGwGwQ)

     笔者使用的是linode，所以就用linode作为范例，其他几家基本相同。打开linode官网[linode](https://www.linode.com/)，进行注册。注意在注册邮箱中不能使用163、QQ邮箱等国内免费邮箱，可以使用gmail。

![image](http://upload-images.jianshu.io/upload_images/11740824-383a6c046412e7ee?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    之后点击邮箱中的注册链接完成注册，在注册过程中，需要先向账户中冲入$5来激活账户，放心，这$5以后可以用来购买VPS服务，并不会浪费掉。

    在选择节点之前，强烈建议各位在本地Ping一下到各节点的延迟和丢包情况，测速链接如下：

Facility     HostnameTest                                     Download

Tokyo,     JPspeedtest.tokyo.linode.com             [100MB-tokyo.bin](http://speedtest.tokyo.linode.com/100MB-tokyo.bin)

London,   UKspeedtest.london.linode.com         [100MB-london.bin](http://speedtest.london.linode.com/100MB-london.bin)

Newark,   NJspeedtest.newark.linode.com         [100MB-newark.bin](http://speedtest.newark.linode.com/100MB-newark.bin)

Atlanta,   GAspeedtest.atlanta.linode.com          [100MB-atlanta.bin](http://speedtest.atlanta.linode.com/100MB-atlanta.bin)

Dallas,   TXspeedtest.dallas.linode.com              [100MB-dallas.bin](http://speedtest.dallas.linode.com/100MB-dallas.bin)

Fremont,   CAspeedtest.fremont.linode.com        [100MB-fremont.bin](http://speedtest.fremont.linode.com/100MB-fremont.bin)

    可以下载后面附的文件来测速，也可以在本地Ping一下各节点的地址来测试。另外虽然东京的节点状况比较良好，但笔者并不太推荐东京的节点。因为随着国内在东京节点中开的服务器增多，很多东京的IP都已经被墙掉了，所以虽然你Ping的状况良好，但实际开通之后还是有很大几率连接不上，需要联系linode官方给你更换服务中心的。以上就是笔者的惨痛经历。

# 添加机器

    注册成功之后登陆，然后添加一台机器。

![image](http://upload-images.jianshu.io/upload_images/11740824-6dbc24721d36571d?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    选择你想要的计费方式，然后注意在location中选择自己想要购买的机器所在位置，之后添加。

    开通之后，选择需要安装的系统等，设置密码。

![image](http://upload-images.jianshu.io/upload_images/11740824-6d28997da9de1fb7?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    安装完成后，就可以看到自己的机器了

![image](http://upload-images.jianshu.io/upload_images/11740824-29863a1184e56d1e?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    点击进入，可以看到自己机器的大致情况

![image](http://upload-images.jianshu.io/upload_images/11740824-7df55c3d60a3afe6?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    首先需要在右边将机器切换成运行状态，之后点击上面的标签页Remote Access，其中可以看到自己的机器的IP地址

![image](http://upload-images.jianshu.io/upload_images/11740824-78765142b1314256?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 连接机器

    之后，需要使用ssh连接自己的机器，可以使用putty和Xshell。推荐使用Xshell，相对更好上手。    

    下载安装Xshell之后，打开，新建一个会话

![image](http://upload-images.jianshu.io/upload_images/11740824-7b070902c901e710?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    在主机中填入自己搭建的机器的IP地址，也就是上文中Remote Access中的IP地址，名称可以随意修改成自己喜欢的名称。

![image](http://upload-images.jianshu.io/upload_images/11740824-93880f3255e4beb5?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

之后，点击用户身份验证，用户名是搭建机器时设置的用户名，默认为root，密码则是搭建机器时设置的密码

![image](http://upload-images.jianshu.io/upload_images/11740824-4a80c5ac70913ce7?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    在终端中，修改编码为Unicode（UTF-8）

![image](http://upload-images.jianshu.io/upload_images/11740824-d8c0dde053309173?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

    之后确定，在会话中点击刚才设置的会话，点击连接，成功之后应该是下图所示

![image](http://upload-images.jianshu.io/upload_images/11740824-20488f02441094e1?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 安装ssss

   之后开始给服务器安装ShadowSocks，首先使用命令 update-grub更新内核

root@localhost:~# update-grub

Generating grub configuration file ..

.Found linux image: /boot/vmlinuz-4.4.0-36-generic

Found initrd image: /boot/initrd.img-4.4.0-36-generic

done

root@localhost:~#

然后使用一键脚本安装ss

wget -N --no-check-certificate https://github.com/Sherlockwoo/shadowsocksR_1nstall/raw/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh

执行命令之后会让你输入数字选择选项，输入1，选择安装，在安装过程中可以一路回车，保持默认设置。

请输入要设置的ShadowsocksR账号 端口

(默认:2333):

—————————————————————————————— 

端口 :2333

——————————————————————————————

请输入要设置的ShadowsocksR账号 密码

(默认: doub.io):

——————————————————————————————

 密码 : doub.io

——————————————————————————————

请选择要设置的ShadowsocksR账号 加密方式

1.rc4-md5

2.aes-128-ctr

3.aes-256-ctr

4.aes-256-cfb

5.aes-25

6-cfb86.camellia-256-cfb

7.chacha20

8.chacha20-ietf

注意：chacha20-*系列加密方式，需要额外安装依赖 libsodium ，否则会无法启动ShadowsocksR!

(默认:2.aes-128-ctr):

—————————————————————————————— 

加密 : aes-128-ctr

——————————————————————————————

请选择要设置的ShadowsocksR账号 协议插件

1.origin

2.auth_sha1_v4

3.auth_aes128_md5

4.auth_aes128_sha1

(默认:2.auth_sha1_v4):

—————————————————————————————— 

协议 : auth_sha1_v4

——————————————————————————————

是否设置 协议插件兼容原版(_compatible)？[Y/n]

请选择要设置的ShadowsocksR账号 混淆插件

1\. plain

2\. http_simple

3\. http_post

4\. random_head

5\. tls1.2_ticket_auth

(默认: 5\. tls1.2_ticket_auth):

——————————————————————————————

混淆 : tls1.2_ticket_auth

——————————————————————————————

是否设置 混淆插件兼容原版(_compatible)？[Y/n]

请输入要设置的ShadowsocksR账号 欲限制的设备数

 ( auth_* 系列协议 不兼容原版才有效 )[注意] 设备数限制：每个端口同一时间能链接的客户端数量(多端口模式，每个端口都是独立计算)，建议最少 2个。

(默认: 无限):5

——————————————————————————————

链接设备数 : 5

——————————————————————————————

请输入要设置的每个端口 单线程 限速上限(单位：KB/S)[注意] 单线程限速：每个端口 单线程的限速上限，多线程即无效。

(默认: 无限):666

——————————————————————————————

单端口单线程 : 666 KB/S

——————————————————————————————

请输入要设置的每个端口 总速度 限速上限(单位：KB/S)[注意] 端口总限速：每个端口 总速度 限速上限，单个端口整体限速。

(默认: 无限):2333

——————————————————————————————

单端口总限速 : 2333 KB/S

——————————————————————————————

同时最后也会提示是否设置 混淆 兼容原版（也就是使用原版55也能链接），不懂 直接回车 或 输入 y 。（协议不在兼容原版）

注意：关于限制设备数数，这个协议必须是非原版并且不兼容原版才有效，也就是必须55R客户端使用协议的情况下，才有效！

不输入一路回车就是 默认参数：

端口 : 2333

密码 : doub.io

加密 : aes-128-ctr

协议 : auth_sha1_v4_compatible

混淆 : tls1.2_ticket_auth_compatible

设备数限制: 0(无限)

单线程限速: 0 KB/S (不限速)

端口总限速: 0 KB/S (不限速)

如果安装过程没有出错，那么最后就会提示：

############################################################

ShadowsocksR账号 配置信息： 

I P    : xxx.xxx.xxx.xxx 

端口    :2333

密码    : doub.io 

加密    : aes-128-ctr 

协议    : auth_sha1_v4_

compatible 混淆    : tls1.2_ticket_auth_compatible 

 设备数限制:5单

线程限速:666KB/S  

端口总限速:2333KB/S

55链接:ss://xxxxxxxxxxxxx

55二维码:http://pan.baidu.com/share/qrcode?w=300&h=300&url=ss://xxxxxxxxxxxxx

55R链接:ssr://xxxxxxxxxxxxx

55R二维码:http://pan.baidu.com/share/qrcode?w=300&h=300&url=ssr://xxxxxxxxxxxxx

 提示:  在浏览器中，打开二维码链接，就可以看到二维码图片。 协议和混淆后面的[ _compatible ]，指的是 兼容原版协议/混淆。############################################################

    注意记住设置的端口号和密码

# 安装BBR加速

    安装BBR加速，执行以下命令

wget -N --no-check-certificate https://github.com/Sherlockwoo/shadowsocksR_1nstall/raw/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh

    输入数字15，然后输入1 ，进行安装。 

    安装成功后会提示重启vps，重启后再次执行一键安装脚本： 

    输入数字15，然后输入2，启动服务。

# 下载ShadowSocks客户端

     之后，下载ss客户端

    1\. Windows客户端下载地址：Windows对Framework的版本要求比价高，我的是4.0.2的要求Framework4.6.2。如果是XP或者Framework比较低的，可以直接下载低版本的ss（windows 2.3.1下载地址：[https://github.com/shadowsocks/shadowsocks-windows/releases?after=2.5.1](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-windows/releases?after=2.5.1)）。

    2\. Mac客户端下载地址：[https://github.com/shadowsocks/ShadowsocksX-NG/releases](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/ShadowsocksX-NG/releases)。

    3\. Linux客户端下载地址：[https://github.com/shadowsocks/shadowsocks-qt5/wiki/Installation](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-qt5/wiki/Installation)。

    4\. Android/安卓客户端下载地址：[https://github.com/shadowsocks/shadowsocks-android/releases](https://www.flyzy2005.com/go/go.php?url=https://github.com/shadowsocks/shadowsocks-android/releases)。

    5\. iOS/苹果客户端直接在App Store里搜索shadowsock关键字（或者wingy关键字，FirstWingy可用 2018.03.25），软件经常被下架，我目前用的是Wingy & Shadowrocket~如果找不到，你也可以通过**PP助手**去下载Shadowrocket。

    或者使用百度云下载

    百度云下载链接：[https://pan.baidu.com/s/1GgzKSzEmqctQ5MUvQ4RR1g](https://www.flyzy2005.com/go/go.php?url=https://pan.baidu.com/s/1GgzKSzEmqctQ5MUvQ4RR1g) 密码：e66v

    下载打开之后，在服务器IP中输入搭建的机器的IP，端口输入在ShadowSocks中设置的端口，密码也是ShadowSocks中设置的密码，之后点击确定，然后右键图标，选择启用代理模式。之后尽情享用吧！！

![image](http://upload-images.jianshu.io/upload_images/11740824-74635967f3dcb94b?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

# 请求帮助

    PS:如果连接发生问题，可以点击linode中的Support页签，发起一个ticket，请求帮助。

![image](http://upload-images.jianshu.io/upload_images/11740824-20fa1d3e9c8212d9?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
