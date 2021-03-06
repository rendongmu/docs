# 服务器部署
服务器提供[社区版](https://github.com/wildfirechat/server/releases)和[Demo应用服务](https://github.com/wildfirechat/app_server/releases)软件。社区版是IM通讯服务器，负责发送消息等IM业务；Demo服务是模拟客户的应用服务，提供登陆等功能。

## 环境需求
Windows/Linux/MacOS都可以，需要JRE1.8以上，需要网络环境。如果没有公网IP，也可以在局域网内体验。需要开通```1883```、```80```和```8888```端口。

## 野火IM服务器的部署
#### 配置修改
社区版软件下载 **（[点这儿去下载编译好的软件包](https://github.com/wildfirechat/server/releases)，如果想自行编译的话，请用git clone整个仓库下来，别打包下载zip压缩包，压缩包会编译错误！源码下载后不能直接运行，需要编译，编译方法参考源码中的```README.md```，编译完成后按照readme的说明找到软件包）** 解压后，修改```/config/wildfirechat.conf```文件，修改```http_port```为80，修改```server.ip```为服务器ip地址。***注意一定要改成客户端可以访问的地址，不能用127.0.0.1或localhost***, ***另外要注意是使用软件包，不是源码，如果您下载的是源码的话需要先编译***。
>> 这里有个限制http_port必须为80端口，如果使用其它端口，在使用七牛文件服务器时，发送媒体消息会失败
>> 需要注意软件包和源码的区别，这里操作的是软件包不是源码，如果您下载的源码可以按照说明编译出软件包来进行配置和运行。

#### 运行

**注意一定到在```bin```的同级目录下执行命令，不要到```bin```内执行**

#####mac/linux系统

  1. 命令行到解压目录

  2. **使用root用户**，执行``` sh ./bin/wildfirechat.sh```


#####windows系统

1. 使用命令行窗口执行```bin\wildfirechat.bat```（双击执行不可用，必须命令行)。

> 在windows下编辑过，可能会保存为windows格式，在放到linux上执行时，有可能会出现错误，处理方法请参考[FAQ](http://docs.wildfirechat.cn/faq/server.html)


执行相应系统的启动命令之后，等待10秒钟后，在浏览器中输入```http://${服务器的IP}/api/version```，查看版本信息。

## Demo应用服务器的部署
#### 配置修改
app软件下载解压后，修改```/config/sms.properties```文件，设置```superCode```为```66666```
>> 发送短信需要购买短信服务，在没有短信服务的情况下，使用superCode作为验证码来登陆。
>> 下载地址在本文的最开头处，同样需要使用软件包，如果是源码需要先编译。

#### 运行
执行```java -jar app-0.0.1-SNAPSHOT.jar```。

#### 检查程序可用性
等待10秒钟，在浏览器中输入```http://${服务器的IP}:8888/```，查看是否返回OK。
