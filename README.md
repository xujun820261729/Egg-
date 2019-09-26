# Egg
  egg.js是基于koa为底层，由阿里nodejs团队封装的企业级Web应用解决方案，以约束和规范化团队开发，帮助开发团队和开发人员降低开发和维护成本为核心设计理念的优秀解决方案

### 层次关系
1. View:作为用户的 视图表现 部分，常见的展示形式如浏览器作为载体的网页、原生APP应用界面、桌面应用界面等，用于提供用户界面以便收集、响应用户行为产生的数据；
2. Controller:作为 控制器层 部分，控制用户界面（View）的数据流转途径，主要行为包含接收用户数据请求、发送请求至业务层（Service）、获取业务层（Service）数据响应，将响应数据发送至用户界面（View），或生成相应的模板界面发送至用户；
3. Service：作为 业务处理层 部分，主要负责收集及对数据进行相应的运算处理，主要行为包含收集控制器请求数据、数据有效性验证、运算、请求数据模型（Model）、接收数据模型（Model）响应消息、响应结果至控制器等；
4. Model：作为 数据模型层 部分，主要用于将数据持久化（OUT）、查询持久化数据（IN），常见行为如对数据库进行操作、缓存数据库数据等；

### 路由（Router）
定义: 通过统一的配置，我们可以避免路由规则逻辑散落在多个地方，从而出现未知的冲突，集中在一起我们可以更方便的来查看全局的路由规则。

### 内置对象
1. 由 Koa 继承的对象：Application、Context、Request、Response
2. 框架扩展的对象：Controller、Service、Helper、Config、Logger
3. 详情:查看Docs中的 对象解析

###  中间件(MiddleWare)
 Egg 约定一个中间件是一个放置在 app/middleware/ 下的独立文件，并会 exports 一个函数
- 参数:
    1. options: 中间件的配置项，框架会将 app.config[${middlewareName}] 传递进来。
    2. app: 当前应用 Application 的实例。
- 多个中间件时
    1. config.middleware = ['mw1', 'mw2', 'mw3']; ，则中间件的加载顺序为：mw1 -> mw2 -> mw3


### 更简单的拦截处理
中间件已配备了几个通用参数，用以更简便的设置中间件的状态,重置config文件的
1.  enable [boolean] 控制中间件是否开启
2.  match [string、stringp、RegEx、function] 设置只有符合某些规则的请求前缀才会经过这个中间件
3. ignore [string、stringp、RegEx、function] 设置符合某些规则的请求前缀不经过这个中间件

