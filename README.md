# NetCore22MongoDBNLog
Net Core2.2 Nlog MongoDB
NET Core 实战：使用 NLog 将日志信息记录到 MongoDB
        在项目开发中，日志系统是系统的一个重要组成模块，通过在程序中记录运行日志、错误日志，可以让我们对于系统的运行情况做到很好的掌控。同时，收集日志不仅仅可以用于诊断排查错误，由于日志同样也是大量的数据，通过对这些数据进行集中分析，可以产生极大的价值。
　　在微服务的系统架构中，由于一个系统会被拆成很多个功能模块，每个模块负责不同的功能，对于日志系统的要求也会更高，比较常见的有 EFLK(ElasticSearch + Filebeat + LogStash + Kibana) 方案，而对于我们这种单体应用来说，由于程序的代码比较集中，所以我们主要采用手写日志帮助类或是使用第三方组件的形式进行日志信息的记录。
  　1、为什么选择 NLog 和 MongoDB
　　在 ASP.NET Core 中，巨硬为我们提供了一个 ILogger 接口，通过 ILogger 接口，我们可以很方便的将日志信息输出到控制台中，不过，在控制台中查看日志信息会显得不太方便，因此，我们可以通过实现该接口或是直接使用第三方的框架来实现将日志信息记录到别的存储介质中。

　　在 .NET Framework 时代，对于第三方的日志框架的选择，绝大多数童鞋首选的都会是 log4net 这一根据 Log4j 移植的日志框架，不过，由于 log4net 目前已经接近有3年的时间没更新了，所以就不在考虑范围内。综合比较下官方文档中推荐的几款第三方日志框架，最终还是选择 NLog 这一目前使用人数相对来说比较多的框架，毕竟用户多的话，遇到什么问题也好找资料。

　　通常，我们会将日志信息记录到 txt or log 文件中，虽然你可以通过修改日志布局让日志信息具有良好的可读性，不过在信息多的情况下查阅时还是会显得不太方便。因为不仅做到对于错误信息做到记录，还需要记录程序在运行时的访问日志，所以将日志信息写入到关系型数据库中就不是特别合适了。

　　而 MongoDB 作为一个文档型的 NoSQL 数据库，相比于传统的关系型数据库，NoSQL 数据库具有更好的扩展性、以及能提供更出色的性能，因此，我最终选择将日志信息记录到 MongoDB 中。

//切换到 admin 数据库
use admin

//创建一个管理员用户
db.createUser(
   {
     user: "user name",
     pwd: "user password",
     roles: [ { role: "root", db: "admin" } ]
   }
)

//切换到 admin 数据库
use GrapefruitVuCore

//创建一个管理员用户
db.createUser(
   {
     user: "grapefruit",
     pwd: "grapefruit",
     roles: [ { role: "readWrite", db: "GrapefruitVuCore" } ]
   }
)


https://www.cnblogs.com/Leo_wl/p/10232312.html
