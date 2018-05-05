# Ubuntu下安装mysql

## 更换阿里源
- 备份旧的源文件
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak #备份
sudo vim /etc/apt/sources.list #修改
sudo apt-get update #更新列表
```
- 更换源文件为
```
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
```
## 安装mysql
```
sudo apt-get install mysql-server mysql-client
```
如果出现，需要依赖 mysql-server-5.5 mysql-client-5.5，逐一安装依赖（可能会陷入依赖无底洞）

```
sudo apt-get install aptitude
```
使用这个工具，当某个库依赖的库与当前版本不一致时，aptitude 会尝试降级当前这个库的版本，同时解决降级这个库对其它软件的依赖性的影响， 最终成功安装apt-get 没法安装的软件

```
sudo aptitude install mysql-server mysql-client
```
一路输入 Y
## 设置mysql root用户密码
安装过程中会让你输入root用户(管理Mysql用户，非ubuntu系统用户)密码，按照要求输入即可

## 验证安装
```
sudo netstat -tap |grep mysql
```
出现以下结果，表示安装成功
```
zhaoqi@zhaoqi-Inspiron-7557:/media/zhaoqi/FCF0AA56F0AA1744/Reading Notes/Mysql$ sudo netstat -tap | grep mysql
tcp6       0      0 [::]:mysql              [::]:*                  LISTEN      21845/mysqld        
tcp6       0      0 [::]:33060              [::]:*                  LISTEN      21845/mysqld        
```
## 进入mysql
切换root    
```
mysql -uroot -p
```
```
root@zhaoqi-Inspiron-7557:/media/zhaoqi/FCF0AA56F0AA1744/Reading Notes/Mysql# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.11 MySQL Community Server - GPL

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
mysql> 
```
