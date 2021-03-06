什么是Twitter2Sina
=============

Twitter2Sina是一个自助式的web程序，帮助您将Twitter推文自动同步到新浪微博。您只需要登陆一次完成设置后，每隔2分钟，您的新推文将会自动被同步到绑定的新浪微博上去。

为什么选用Twitter2Sina
=============

## 特性

- 基于Google App Engine构建
 - GAE方便搭建，使用简单，不收取任何费用。

- 支持Twitter和新浪微博的OAuth认证
 - Twitter和新浪微博均使用OAuth认证登陆，系统不会保存您的密码，更安全。同时，使用Twitter OAuth认证可以摆脱每分钟只能请求150次的限制。
  
- 回复的推文将不会被同步到新浪微博
 - 考虑到回复性推文同步到新浪后别人也不容易看懂，所以以@开头的回复性推文将不会被同步。

=======

- 带有\#nosina便签的推文将不会被同步到新浪微博
 - 有时你可能不希望有些推文被同步，so easy，加上\#nosina便签即可。
  
- 推文中的@username将被替换
 - 考虑到新浪微博中有时可能不存在与Twitter中相同的用户名，同时也处于保护他人隐私的需要，推文中的@username将被替换成[username]。
  
- 推文中的RT和#tag将被替换
 - 为符合新浪微博的习惯，推文中的RT将被替换成“转发自”，推文中的\#tag将被替换为\#tag\#。
  
- 支持同步带链接的推文(new)
 - 所有推文中的链接在Twitter中都被缩短为t.co/xxx，而t.co被新浪认为是非法链接而屏蔽。现在程序支持将包含t.co的链接展开再进行同步。
  
- 来自街旁网的推文将不会被同步
 - 由于街旁网支持同时将信息同步到新浪微博和Twitter(需使用vpn登陆 http://tw.jiepang.com 进行设置)，所以为避免重复，本程序将不同步来自于街旁网的推文。

- 来自Instagram的推文将不会被同步
 - 请使用第三方应用同步Instagram的推文，因为第三方的应用同步后可以显示照片，如InstaWeibo。

如何搭建
=============

- 注册自己的GAE应用 
 - 前往Google App Engine(https://appengine.google.com)
 - 第一次开通GAE可能需要提供手机号。
  
- 注册自己的Twitter app key (需翻墙)
 - 前往Twitter开发者中心(https://dev.twitter.com)
 - 注册过程中的callback url为空，完成后记录下Consumer key和Consumer secret。 
  
- 注册自己的新浪微博app key
 - 前往新浪微博开发者中心(http://open.weibo.com)
 - 注册过程中类型选择其他，完成后记录下App Key和App Secret。
 - 注：oauth的回调地址为http://你的gae地址/oauth
  
- 下载代码并修改配置
 - 将代码下载到本地。
 - 打开twitter2sina.py，将15-19行改为上面注册好的新浪app key、secret、callback和Twitter app key、secret。
 - 打开app.yaml将第一行的tui2lang改为自己注册的GAE应用名称。
  
- 将代码上传到GAE
 - 下载 Google App Engine SDK for Python(http://code.google.com/appengine/downloads.html) 或使用其他方式将代码传送到您的GAE上。
  
如何使用
=============

- 登陆您的GAE应用，网址一般为 您的应用名.appspot.com (需翻墙)。
- 点击Sina Oauth首先完成新浪微博的认证，然后页面跳转将会自动填充好你的新浪微博昵称
- 输入Twitter用户名，点击Get Twitter Oauth Pin完成Twitter的 
OAuth认证，将得到的一串数字输入到Twitter Oauth PIN中(需翻墙)。
- 最后点击submit，若配置成功将会同步您的最近一条推文。
- 配置成功后，以后每2分钟同步一次。


=======

## 理论上一个Twitter2Sina程序支持多用户，但新浪微博中未通过审核的应用每天都有请求次数限制，所以最好一个人使用。

## 新浪微博目前的政策是未审核应用的Oauth有效期为一天，所以每天都需要认证一下，目前没找到什么解决方案。。。

后话
=============
  
欢迎对代码及相关功能进行改进，有任何问题请联系 pilixiaoxuanfeng AT gmail.com
