# error
## 数据库
### 事务隔离级别和事务隔离解决的问题
          更新丢失    脏读   不可重复读     幻读
未提交读    true     false     false       true
已提交读    true     true      false       false
可重复读    true     true       true       false   
串行化      true     true       true       true

## 网络
### http和https的区别
https是加密后的http
https加密方式：https://segmentfault.com/a/1190000019687184

### cookie和session的区别
cookie是在客户端
      cookie是一小段文本信息，客户端把cookie保存在本地文件夹，文本形式保存；
      cookie是不可以跨域名的；
      中文属于Unicode字符，内存中占4个字符，英文属于ASCALL，内存中占2个字符；cookie要使用unicode字符要进行编码，否则会乱码。
      cookie的生命周期：maxAge==0删除该cookie；maxAge>0在规定的时间内都有效；maxAge<0只在本窗口打开的子窗口有效。
      cookie不提供删除和修改，删除maxAge=0;修改新建cookie修改value并覆盖。
      
session在服务端
       session对象在客户端第一次请求服务器的时候创建。多个客户端执行程序，服务器会保留多个session，但是当前客户端只会获取到自己的session。
       session生命周期：每个用户会有独立的session，当内容过于复杂，会导致内存溢出。只访问静态资源不会创建session，访问jsp和servlet等会创建session。每访问一次服务器，就会认为该用户的session active一次。设置session的超时时间，会删除session，属性是maxInactiveInterval。可以调用session的invalidate（）方法。
 
总结：
1.coookie在客户的浏览器上，session在服务器上。
2.cookie不是很安全，本地文件可以分析，并进行cookie欺骗
3.cookie可以设置过期时间使它过期，session也有超时时间
4.session保存的过多会比较占用服务器性能，考虑性能方面，需要使用cookie
5.cookie保存的数据大小和数量都有限制，session没有
       
### cookie和session的联系
        虽然Session保存在服务器，对客户端是透明的，它的正常运行仍然需要客户端浏览器的支持。这是因为Session需要使用Cookie作为识别标志。HTTP协议是无状态的，Session不能依据HTTP连接来判断是否为同一客户，因此服务器向客户端浏览器发送一个名为JSESSIONID的Cookie，它的值为该Session的id（也就是HttpSession.getId()的返回值）。Session依据该Cookie来识别是否为同一用户
        
         ---假如不支持cookie---
         url地址重写
         将用户的session的id西岛url地址中，服务器解析后获得session的id
