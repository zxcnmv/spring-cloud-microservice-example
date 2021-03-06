[![JDK](http://img.shields.io/badge/JDK-v8.0-yellow.svg)](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
[![Build](http://img.shields.io/badge/Build-Maven_2-green.svg)](https://maven.apache.org/)
[![License](http://img.shields.io/badge/License-Apache_2-red.svg)](http://www.apache.org/licenses/LICENSE-2.0)

## 简介

本项目是一个演示项目，旨在演示`SpringCloud`框架的一些基本功能。本项目包含以下几个子模块`(module)`

* `common` - 通用代码
* `api-gateway` - 服务网关
* `discovery` - 服务注册与发现节点
* `config-service` - 配置中心
* `compute-service` - 计算服务
* `ui` - WEB图形接口，即服务的消费者

为了方便起见，以上除`common`以外的模块，都将分别构建成`docker`镜像，并通过`docker-compose`工具启动。

本项目包含以下features的演示

1. 服务发现与注册
2. 服务的消费
3. 服务断熔机制
4. 服务的负载均衡
5. 配置中心化
6. 服务网关

## 构建镜像

下载代码到本地，使用一下`maven`指令即可完成。

```bash
mvn clean package
mvn -f api-gateway/pom.xml docker:build
mvn -f discovery/pom.xml docker:build
mvn -f config-service/pom.xml docker:build
mvn -f compute-service/pom.xml docker:build
mvn -f ui/pom.xml docker:build
```

## 启动

拷贝[docker-compose.yml](docker-compose.yml)到`docker`宿主机的某个目录。

```bash
docker-compose -f /path/to/docker-compose.yml up -d
```

如果启动成功，

* 访问`http://HOST:8761/dashboard`可查看被注册的服务的详情。
* 访问`http://HOST:8866/ui`可查调用分布式服务并展示结果。

> 注意: HOST指`docker`宿主机名或IP地址

## 许可证

[Apache 2.0](LICENSE)

## 联系我

![QQ](http://img.shields.io/badge/QQ-23007067-blue.svg)
![WeChat](http://img.shields.io/badge/WeChat-yingzhor-blue.svg)
![Email](http://img.shields.io/badge/Email-yingzhor@gmail.com-blue.svg)
