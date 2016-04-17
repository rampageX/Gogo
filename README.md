#部署

fork https://github.com/Kisesy/Gogo 到自己 GitHub

在 heroku 新建个 app，建完之后在部署页面(deploy)有个 Deployment method，选成 Githu，点击下面的 Connect to GitHub 连接好 GiHub 账号后，
搜索框里写上 "gogo"，点搜索，选上刚才 fork 的 Gogo

点上面的 settings 页，有个 Buildpacks 点击 add Buildpack
填上 https://github.com/heroku/heroku-buildpack-java
然后回到部署页面，点最下面的 Deploy Branch 就行了

这样就完成了 App 的部署

打开客户端 GoGo 里 config 文件夹下的 gogo.conf，把部署的 app 按下面这样写

      "version" : "1.6.0",
      "proxyOnlyForForeignIPs" : "true",
      "apps" : [{
        "app" : "创建App的名字", <==== 关键
        "platform" : "heroku"
      }, {
        "app" : "freetunnel0",
        "platform" : "heroku"
      }, {
        "app" : "freetunnel1",
        "platform" : "heroku"
      }
  
重载 Gogo，打开 http://127.0.0.1:9092/apps 就能看到效果了。
