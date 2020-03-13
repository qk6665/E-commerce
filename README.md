# 简介

本仓库项目是Java+SSM电商后端项目，实现了用户模块、分类模块、商品模块、购物车模块、订单模块、收货模块、支付模块，v1.0是根据Geely老师的慕课网课程一步步做下来的，课程网址是https://coding.imooc.com/class/96.html ，有兴趣的同学可以学习。

# 环境依赖

JDK: v1.8.0_231

Tomcat: v7.0.75（编码设置为UTF-8）

Maven: 3.6.3

MySQL: 5.7.29



# 部署步骤

### 建立数据库

将tools/mmall.sql运行到数据库服务器上，编码设置为UTF-8，并将src/main/resources/datasource.properties中的db.url、db.username、db.password设置为db对应的地址、账号、密码，db.driverLocation设置为tools/mysql-connector-java-5.1.6.jar的**绝对路径**。

### 配置文件

src/main/resources/mmall.properties为文件服务器配置，mmall.properties中的ftp.server.ip、ftp.user、ftp.pass、ftp.server.http.prefix修改为文件服务器的ip、用户名、密码、地址，alipay.callback.url修改为/order/alipay_callback.do接口的地址。

src/main/resources/logback.xml为日志配置，其中两个File和两个fileNamePattern标签对应了运行日志和错误日志的绝对路径，建议设置在Tomcat根目录下的logs文件夹中。

src/main/resources/zfbinfo.properties为支付宝支付模块的配置，不使用可以不配置。按https://docs.open.alipay.com/200/105311/ 所示的教程建立支付宝沙箱账号，模拟支付宝收付款。支付宝密钥采用SHA256withRsa，需要使用RSA工具生成。zfbinfo.properties中的pid、appid、private_key、public_key、alipay_public_key设置为沙箱账号中对应的值。再将src/main/webapp/WEB-INF/lib目录下的四个jar包导入项目配置中。

### 编译

```
mvn clean package -Dmaven.test.skip=true
```

### 运行

在生成的target目录下将编译生成的war文件移动到Tomcat根目录下的webapps目录下，在Tomcat根目录下的bin目录下运行startup.sh，启动服务器。

### 关闭

在Tomcat根目录下的bin目录下运行shutdown.sh，关闭服务器。



# 目录结构

```
├── src
│   ├── main                  // 主文件
│   │   ├── java              // 包
│   │   ├── resources         // xml、properties等静态文件
│   │   └── webapp            // 入口文件
│   └── test                  // 入口js文件
├── tools
│   ├── mmall.sql             // 数据库文件
│   └── mysql-connector-java-5.1.6.jar   // 数据库与java对接jar
├── interface_doc             // 接口文档
│   ├── 接口文档
│   └── mmall.postman_collection.json // 可从postman中improt该文件，导入接口配置
├── .gitignore
├── LICENSE                   // 证书
├── README.md                 // help
└── pom.xml
```



# V1.0 update

包含用户模块、分类模块、商品模块、购物车模块、订单模块、收货模块、支付模块，实现了电商基本业务逻辑。
