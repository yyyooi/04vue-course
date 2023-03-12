配置
	name: 
		git config --global user.name "llr"
	email: 
	    git config --global user.email "liulir_grace@163.com"
使用git
	git status 查看状态
	git init 初始化仓库
	
	刚刚添加到项目中的文件是未跟踪状态
		未跟踪->暂存状态
			git add 文件名 将文件切换到暂存的状态
			git add *
		暂存状态->未修改 （入库）
			git commit -m "xxx" 将暂存的文件存储到仓库中 xxx表示一种日志
			git commit -a -m "xxx" 提交所有已修改文件（未跟踪文件不会提交-----在add之后文件才会被跟踪）
		未修改->已修改
			修改代码即可
常用命令
	重置文件
		git restore filename 表示重置 从已修改到未修改
		git restore --stage 从暂存状态取消
	删除文件
		git rm 文件名 rm表示删除 
		git rm .\1.txt -f 强制删除 已修改未暂存的文件
	移动文件
		git mv from to # 移动文件 重命名文件

分支 每次在源文件改代码之前都先创建一个新的分支
	git在存储文件时 每一次代码提交 都会创建一个与之对应的节点 git就是通过一个一个的节点存储项目 
    节点会构成代码的树状结构 树状结构就意味着存在分支 默认情况下只有一个分支 master
	在使用git时 可以创建多个分支 分支和分支之间是相互独立的 在一个分支上修改代码不会影响其他分支
	 
	git branch 显示分支
	git branch xx 创建新分支
	git branch -d xxx 删除分支xxx
	git switch xxx 切换到xxx分支
	git switch -c xxx 创建一个分支并切换分支 
	
	在开发中都是在自己的分支上修改代码 代码修改后合并到主分支上
	·合并分支：git merge xxx 在该分支下合并xx分支
	
	··在开发中除了通过merge合并分支 还可以通过变基
		我们通过merge合并分支时 在提交记录中会将所有的分支创建和分支合并的过程全部显示出来
			这样当项目比较复杂 开发过程比较波折时 我们必须要反复创建分支 反复删除分支

变基 对合并后的分支做根部替换操作
	变基时发生了什么？
		·当我们发起变基时 git会找到两条根的共同祖先
		·对比当前分支相对于祖先的历史提交 并且将不同提取出来存到一个临时文件中
		·将当前部分指向目标基底
		·以当前基地开始重新执行历史操作
	变基和合并分支最终结果都一样
		但是变基会使得提交记录更加清晰
	大部分情况下合并和变基可以互换 但是若是提交到远程仓库 尽量不使用变基
	命令：
		对xxx变基 基底变为yyy
			git switch xxx
			git rebase yyy
			git switch yyy
			git merge xxx
			git branch -d xxx
			
远程仓库
	上述都在本地进行 但是在开发中显然不能这样 这时我们需要远程的git仓库
	 不同点在于 远程仓库可以被多人共同使用 协同开发
	 在实际开发过程中远程服务器通常由公司搭建然后内部使用或者购买一些公共的私有git服务器
	 学习阶段直接使用开放的公共仓库
		目前常用的库
			GitHub
			Gitee
	
	···本地库上传GitHub
	git remote add origin https://github.com/yyyooi/git-demo2.git
	* git remote add <remote name> <url>
	git branch -M main
	* 修改分支的名字为main
	git push -u origin main
	* 将代码上传到服务器上
	
	···本地库上传gitee
	##cd existing_git_repo
	git remote add gitee https://gitee.com/liulir/git-demo.git
	git push -u gitee "main"
	
	···下载别人的git
	新建文件夹在文件夹内新建终端
	git clone https://gitee.com/liulir/git-demo.git
