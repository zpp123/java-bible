# 安装jdk环境

服务器上如果不需要编码实际应该不安装JDK只安装JRE，我们考虑到以后可能安装其他软件就直接装JDK了。

## 下载JDK

[下载jdk](http://stackoverflow.com/questions/10268583/downloading-java-jdk-on-linux-via-wget-is-shown-license-page-instead)

上面的连接是stackoverflow有开发者写的不使用cookie下载jdk和jre的命令。

```bash
[root@localhost ~]#  wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz
--2016-09-09 19:57:01--  http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz
Resolving download.oracle.com... 23.4.240.57, 23.4.240.59
Connecting to download.oracle.com|23.4.240.57|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://120.52.72.24:80/download.oracle.com/c3pr90ntc0td/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz [following]
--2016-09-09 19:57:01--  http://120.52.72.24/download.oracle.com/c3pr90ntc0td/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz
Connecting to 120.52.72.24:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181435897 (173M) [application/x-gzip]
Saving to: “jdk-8u102-linux-x64.tar.gz”

100%[==================================================================================================================================>] 181,435,897 2.07M/s   in 85s     

2016-09-09 19:58:26 (2.04 MB/s) - “jdk-8u102-linux-x64.tar.gz” saved [181435897/181435897]
```

## 解压

```bash
[root@localhost ~]# tar -zxvf jdk-8u102-linux-x64.tar.gz
[root@localhost ~]# mkdir /usr/local/java
[root@localhost ~]# mv jdk1.8.0_102/ /usr/local/java/
```

## 配置环境变量

```bash
[root@localhost ~]# vim /etc/profile
```

在最后一行添加

```bash
# java
export JAVA_HOME=/usr/local/java/jdk1.8.0_102
export JRE_HOME=/usr/local/java/jdk1.8.0_102/jre
export CLASSPATH=.:$JRE_HOME/lib/dt.jar:$JRE_HOME/lib/tools.jar
export PATH=$JRE_HOME/bin:$JRE_HOME/bin:$PATH
```

## 生效

```bash
[root@localhost ~]# source /etc/profile
[root@localhost ~]# java -version
java version "1.8.0_102"
Java(TM) SE Runtime Environment (build 1.8.0_102-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.102-b14, mixed mode)
```
这里我安装的是最新版的JDK。

## links
   * [目录](<README.md>)
   * 上一节: [初始化操作系统](<init-os.md>)
   * 下一节: [安装tomcat](<install-tomcat.md>)