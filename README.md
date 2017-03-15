# HelloJava
我的第一个项目

##一、安装本地Git客户端
这个也不再赘述，下载exe文件，安装，配置环境变量， 
打开命令窗口，键入：git –version，查看版本号，有返回，表示安装成功。否则表示安装失败。


##二、创建git在本地密钥
为了减少每次提交代码都要输入用户名与密码进行认证的繁琐，我们可以用git命令行在生成密钥(id_rsa与id_rsa.pub)。 
其中id_rsa:是本地PC的密钥，id_rsa.pub：是用于上传到github存储的密钥。 
具体操作如下： 
首先输入命令行： 
git config –global user.name “####” 
git config –global user.email “####@qq.com” 
注意：上面的用户名，密码建议跟github账号保持一致。
接下来就是生成密钥： 
ssh-keygen -C ‘####@qq.com” -t rsa 
然后它会提示你输入文件路径来保存密钥，否则会保存在默认路径(/C/用户/用户名/.ssh/id_rsa):
再接下来它会提示：Enter passphrase(empty for no passphrase):这里直接按Enter就好了。 
这样密钥就生成生成功了。
最后验证密钥： 
ssh -v git@github.com 
当它提示：Hi 用户！You’ve successfully authenticated….你就成功了。


##三、配置github账号：
在第二步的基础上，我们用文本编辑器打开id_rsa.pub，复制里面的内容。 
登录github,点击settings 
 
接下来配置密钥：点击New SSH key 
 
##四、在Github上创建一个仓库，用来存放工程


##五、git命令上传工程至github
首页cd到项目根目录， 
然后初始化git,生成本地git管理: 
git init 
接下来克隆指定项目仓库：git clone 
git clone https://github.com/SunnyLy/SunnyDemoProjectNewest.git 
这就是git与svn的最大不同，每个人都可以复制一个项目的版本另行开发，互不干扰。
再接下来就是把项目工程文件add进去： 
git add ./ (这是无任何过滤，全部添加进去) 
如果要过滤某文件，在.gitignore文件里面配置。
添加完成后，先把代码提交到本地源码库，并填写自己的注释。 
git commit -m “增加了用户体验，修改了一个小bug“
添加完成后，接下来就可以利用push把项目发布到Github上了， 
git push https://github.com/SunnyLy/SunnyDemoProjectNewest.git 
在这里，如果每次push或pull都要输入仓库版本路径很麻烦，我们可以把这个版本路径用一个名字代替origin/master 
如下： 
git remote add origin https://github.com/SunnyLy/SunnyDemoProjectNewest.git
这样push的地址就可以直接用origin来代替 
push代码： 
git push -u origin 
如果有设分支master，直接push到分支的话，用git push -u origin master
当然在push之前，如果要从github上刷新 一下的话，可以用git pull origin
以上，就是git版本管理的几个简单应用。

