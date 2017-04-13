# git 使用手册

---
##一：Git是什么？<br>
	Git是目前世界上最先进的分布式版本控制系统。<br><br>
##二：SVN与Git的最主要的区别？
 `SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而干活的时候，用的都是自己的电脑，所以首先要从中央服务器哪里得到最新的版本，然后干活，干完后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，如果在局域网还可以，带宽够大，速度够快，如果在互联网下，如果网速慢的话，就纳闷了。
 <br> <br>
 Git是分布式版本控制系统，那么它就没有中央服务器的，每个人的电脑就是一个完整的版本库，这样，工作的时候就不需要联网了，因为版本都是在自己的电脑上。既然每个人的电脑都有一个完整的版本库，那多个人如何协作呢？比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。
##三：在windows上如何安装Git？
 * git下载地址[点击下载](http://www.so.com/link?url=http%3A%2F%2Fsoftdl.360tpcdn.com%2FGit%2FGit_2.12.exe&q=git&ts=1492075231&t=2cf004b0dd9c65921ecefdfa083c7c0&src=haosou)
* 下载完成后默认安装。安装完成后，在开始菜单里找到“Git –> Git Bash”,如下： 


	![1](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyr8oschj2071021glh.jpg)
<br>
会弹出一个类似的命令窗口的东西，就说明Git安装成功。如下：

![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyr6clzzj20ik0akq3e.jpg)
<br><br>
安装完成后，还需要最后一步设置，在命令行输入如下：
![](http://ww2.sinaimg.cn/mw690/6941baebgw1eloyr4qsztj20hy05xt9c.jpg)
<br><br>
 因为Git是分布式版本控制系统，所以需要填写用户名和邮箱作为一个标识。
<br><br>
  注意：git config  –global 参数，有了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然你也可以对某个仓库指定的不同的用户名和邮箱。
##四：如何操作？
###一：创建版本库。
　　什么是版本库？版本库又名仓库，英文名repository,你可以简单的理解一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改，删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻还可以将文件”还原”。  

　　所以创建一个版本库也非常简单，如下我是D盘 –> www下 目录下新建一个testgit版本库。  
>cd D:  
>md testgit  
>cd testgit  
>dir   
   
dir是显示当前目录   
1. 通过命令 git init 把这个目录变成git可以管理的仓库，如下：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyr2rpcnj20en025mx9.jpg)  
 
 这时候你当前testgit目录下会多了一个.git的目录，这个目录是Git来跟踪管理版本的，没事千万不要手动乱改这个目录里面的文件，否则，会把git仓库给破坏了。如下：![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyr1x3lzj20h004tgm1.jpg)  
2.  把文件添加到版本库中。  
    　　首先要明确下，所有的版本控制系统，只能跟踪文本文件的改动，比如txt文件，网页，所有程序的代码等，Git也不列外，版本控制系统可以告诉你每次的改动，但是图片，视频这些二进制文件，虽能也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是知道图片从1kb变成2kb，但是到底改了啥，版本控制也不知道。
  
###流程  
我在版本库testgit目录下新建一个记事本文件 readme.txt 内容如下：11111111  

+ 第一步：使用命令 git add readme.txt添加到暂存区里面去。如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyr0wkxbj20ch028dfu.jpg) 如果和上面一样，没有任何提示，说明已经添加成功了。
+   第二步：用命令 git commit告诉Git，把文件提交到仓库。![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyqz56axj20dp03djrr.jpg)  现在我们已经提交了一个readme.txt文件了，我们下面可以通过命令git status来查看是否还有文件未提交，如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyqrg067j20d102zwen.jpg)说明没有任何文件未提交，但是我现在继续来改下readme.txt内容，比如我在下面添加一行2222222222内容，继续使用git status来查看下结果，如下：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyqq7ts6j20h504r74x.jpg)上面的命令告诉我们 readme.txt文件已被修改，但是未被提交的修改。

接下来我想看下readme.txt文件到底改了什么内容，如何查看呢？可以使用如下命令：
git diff readme.txt 如下：
![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyqnrvxgj20ds05maal.jpg)如上可以看到，readme.txt文件内容从一行11111111改成 二行 添加了一行22222222内容。

知道了对readme.txt文件做了什么修改后，我们可以放心的提交到仓库了，提交修改和提交文件是一样的2步(第一步是git add  第二步是：git commit)。

如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyqmcupsj20h609i402.jpg)
###二：版本回退
  
 如上，我们已经学会了修改文件，现在我继续对readme.txt文件进行修改，再增加一行

内容为33333333333333.继续执行命令如下：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyql1473j20cp03vdga.jpg)现在我已经对readme.txt文件做了三次修改了，那么我现在想查看下历史记录，如何查呢？我们现在可以使用命令 git log 演示如下所示：![](http://ww2.sinaimg.cn/mw690/6941baebgw1eloyqd9m1dj20gt08ggn8.jpg)git log命令显示从最近到最远的显示日志，我们可以看到最近三次提交，最近的一次是,增加内容为333333.上一次是添加内容222222，第一次默认是 111111.如果嫌上面显示的信息太多的话，我们可以使用命令 git log –pretty=oneline 演示如下：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyqc3ziwj20gs02paai.jpg) 现在我想使用版本回退操作，我想把当前的版本回退到上一个版本，要使用什么命令呢？可以使用如下2种命令，第一种是：git reset  –hard HEAD^ 那么如果要回退到上上个版本只需把HEAD^ 改成 HEAD^^ 以此类推。那如果要回退到前100个版本的话，使用上面的方法肯定不方便，我们可以使用下面的简便命令操作：git reset  –hard HEAD~100 即可。未回退之前的readme.txt内容如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyqavyf7j20ch04laap.jpg)如果想回退到上一个版本的命令如下操作：![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyqa5xjfj20ct02xaad.jpg)再来查看下 readme.txt内容如下：通过命令type readme.txt查看!http://ww3.sinaimg.cn/mw690/6941baebgw1eloyq9fck2j20c402d74c.jpg可以看到，内容已经回退到上一个版本了。我们可以继续使用git log 来查看下历史记录信息，如下：!![](http://ww2.sinaimg.cn/mw690/6941baebgw1eloyq6bhrlj20dc063dgk.jpg)我们看到 增加333333 内容我们没有看到了，但是现在我想回退到最新的版本，如：有333333的内容要如何恢复呢？我们可以通过版本号回退，使用命令方法如下：

git reset  –hard 版本号 ，但是现在的问题假如我已经关掉过一次命令行或者333内容的版本号我并不知道呢？要如何知道增加3333内容的版本号呢？可以通过如下命令即可获取到版本号：git reflog  演示如下：![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyq5dtfrj20e603e0t5.jpg)通过上面的显示我们可以知道，增加内容3333的版本号是 6fcfc89.我们现在可以命令

git reset  –hard 6fcfc89来恢复了。演示如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyq4m3oqj20e104974t.jpg)可以看到 目前已经是最新的版本了。
###三：理解工作区与暂存区的区别？
工作区：就是你在电脑上看到的目录，比如目录下testgit里的文件(.git隐藏目录版本库除外)。或者以后需要再新建的目录文件等等都属于工作区范畴。

   版本库(Repository)：工作区有一个隐藏目录.git,这个不属于工作区，这是版本库。其中版本库里面存了很多东西，其中最重要的就是stage(暂存区)，还有Git为我们自动创建了第一个分支master,以及指向master的一个指针HEAD。

我们前面说过使用Git提交文件到版本库有两步：

  第一步：是使用 git add 把文件添加进去，实际上就是把文件添加到暂存区。

  第二步：使用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支上。

我们继续使用demo来演示下：

我们在readme.txt再添加一行内容为4444444，接着在目录下新建一个文件为test.txt 内容为test，我们先用命令 git status来查看下状态，如下：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyq3ykzsj20hv06pwfi.jpg)现在我们先使用git add 命令把2个文件都添加到暂存区中，再使用git status来查看下状态，如下：![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyq2gn7sj20d206p0t8.jpg)接着我们可以使用git commit一次性提交到分支上，如下：![](http://ww2.sinaimg.cn/mw690/6941baebgw1eloyq1gpk0j20h704mdgm.jpg)
###四：Git撤销修改和删除文件操作。
一：撤销修改：

   比如我现在在readme.txt文件里面增加一行 内容为555555555555，我们先通过命令查看如下：
  
`type readme.txt`  

![](http://ww3.sinaimg.cn/mw690/6941baebgw1eloyq0rzrcj20ax03vaaa.jpg)在我未提交之前，我发现添加5555555555555内容有误，所以我得马上恢复以前的版本，现在我可以有如下几种方法可以做修改：

第一：如果我知道要删掉那些内容的话，直接手动更改去掉那些需要的文件，然后add添加到暂存区，最后commit掉。

第二：我可以按以前的方法直接恢复到上一个版本。使用 git reset  –hard HEAD^

但是现在我不想使用上面的2种方法，我想直接想使用撤销命令该如何操作呢？首先在做撤销之前，我们可以先用 git status 查看下当前的状态。如下所示：![](http://ww2.sinaimg.cn/mw690/6941baebgw1eloyq034qhj20hs04oaam.jpg)可以发现，Git会告诉你，git checkout  — file 可以丢弃工作区的修改，如下命令：

git checkout  —  readme.txt,如下所示：![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloypz44y5j20eh03w0t4.jpg)
命令 git checkout –readme.txt 意思就是，把readme.txt文件在工作区做的修改全部撤销，这里有2种情况，如下：

readme.txt自动修改后，还没有放到暂存区，使用 撤销修改就回到和版本库一模一样的状态。
另外一种是readme.txt已经放入暂存区了，接着又作了修改，撤销修改就回到添加暂存区后的状态。
对于第二种情况，我想我们继续做demo来看下，假如现在我对readme.txt添加一行 内容为6666666666666，我git add 增加到暂存区后，接着添加内容7777777，我想通过撤销命令让其回到暂存区后的状态。如下所示：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloypybh8pj20h40deq52.jpg)注意：命令git checkout — readme.txt 中的 — 很重要，如果没有 — 的话，那么命令变成创建分支了。

二：删除文件。
假如我现在版本库testgit目录添加一个文件b.txt,然后提交。如下：
   ![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloypxcttej20hr0awmzc.jpg)如上：一般情况下，可以直接在文件目录中把文件删了，或者使用如上rm命令：rm b.txt ，如果我想彻底从版本库中删掉了此文件的话，可以再执行commit命令 提交掉，现在目录是这样的，![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloypvtweyj20jj05cwf4.jpg)只要没有commit之前，如果我想在版本库中恢复此文件如何操作呢？

可以使用如下命令 git checkout  — b.txt，如下所示：![](http://ww4.sinaimg.cn/mw690/6941baebgw1eloyput1l8j20fh06s0tr.jpg)再来看看我们testgit目录，添加了3个文件了。如下所示：![](http://ww1.sinaimg.cn/mw690/6941baebgw1eloyptqfr7j20kz076ab3.jpg)