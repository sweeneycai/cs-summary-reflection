---
title: 操作系统补充
categories:
  - 操作系统
---

# 2018-11-11-操作系统-操作系统补充

* 目录

  {:toc}

## 操作系统 Pro

> 计算机是由以下几个单元组成的：包括输入单元、输出单元、`CPU`内部的控制单元、算数逻辑单元与主存储器五大部分。
>
> `CPU`种类主要有两种：`RISC`-精简指令集 和 `CISC`-复杂指令集。
>
> `RISC`的设计重点在于降低由硬件执行指令的复杂度，因为软件比硬件容易提供更大的灵活性和更高的智能，因此`RISC`设计对编译器有更高的要求；而`CISC`的设计则更侧重于硬件执行指令的功能，使`CISC`的指令变得很复杂。总之`RISC`的指令集精简，执行效率好，但对编译器的要求高，而`CISC`强调硬件的复杂性，指令集多而复杂，执行效率差，但每条指令的功能丰富。
>
> `CPU`频率=外频`*`频，我们常说的超频指的是设定主板的外频或者是倍频为较高频率的一种方式。
>
> 一般主板芯片组有北桥和南桥。北桥称为系统总线，连接`CPU`、内存和显卡等快速设备，南桥称为输入输出总线，连接硬盘、`USB`、`PCI`接口和网卡等慢速设备。

北桥所支持的频率称为前端总线速度，而每次传送的位数则是总线宽度。常见的总线宽度有`32`和`64`位（`bits`），另外所谓的总线带宽则是 前端总线速度`*`总线宽度，即每秒可传送的最大数据量。

> `CPU`每次能够处理的数据量称为字组大小，也有`32`位和`64`位之分，而`32`位`CPU`只能支持最大`4GBytes`的内存。
>
> 内存通常有`SDRAM`和`DDR SDRAM`两种，但`DDR`拥有更快的传输频率，所以`SDRAM`已经逐渐被淘汰啦。
>
> `CPU`内部还存在高速缓存，以提高`CPU`的效率，这里就要用到静态随机存储内存，即`SRAM`，通常容量很小，但速度很快。
>
> `CMOS`芯片是主板上一块可读写的`RAM`芯片，用于保存`BIOS`设置的各项硬件配置信息和用户设定的某些参数，由主板上的纽扣电池供电，即使系统断电信息也不会丢失。而`BIOS`则是主板上的一块`EPROM`或`EEPROM`芯片，用于存放系统重要信息和`BIOS`设置程序。
>
> 显卡内拥有显存，这是因为每个图像的颜色会占用掉内存，而有的显卡甚至拥有`GPU`，用于`3D`加速，这对于游戏是非常重要的性能。
>
> 注意硬盘的结构，拥有扇区（`Sector`）、磁道（`Cylinder`）和`Header`头这几个概念，所以硬盘的总容量计算公式为 `Header`数量`*`每个`Header`负责的磁道数`*`每个磁道所含有的扇区数量`*`每个扇区的字节数。另外我们通常`500GB`的硬盘指的是十进制的`500\*1000\*1000\*1000Bytes`的大小，所以实际上仅拥有`460GBytes`左右的容量。
>
> 计算机中每个设备都有一个`I/O`地址和`IRQ`中断。两个设备不能使用同一个`I/O`地址，而`IRQ`中断是设备联系`CPU`的专门路径，每个设备可以通过`IRQ`中断告知`CPU`自己的工作情况，以方便`CPU`分配任务。
>
> 计算机依次由 硬件--核心（`kernel`）--系统呼叫层（`system call`）--应用程序 这几个部分组成。其中 `kernel`+系统呼叫层+常用的应用程序 组成了现在的操作系统。而`Linux kernel`包含了对硬件进行管理的核心以及向应用程序提供系统调用的接口。
>
> `Linux kernel`分奇数和偶数两种版本，其中偶数版代表稳定版，奇数版代表测试版或不稳定版本。
>
> 硬盘里第一块扇区最重要，一般只有`512bytes`，里面存放着主引导记录（`MBR`）和磁盘分区表（`Partition Table`）。`MBR`主要用来引导启动系统，分区表只能保存四个主分区或逻辑分区，而逻辑分区只能有一个，至于逻辑分区表则保存在逻辑分区的第一个扇区里，因此可以给逻辑分区划分更多的子逻辑分区。
>
> 一般开机的流程是：`BIOS`--`MBR`--`Boot Loader`（`Grub`和`NT5/NT6`等）--`Kernel`。
>
> `Boot Loader`可以存在的地方有两个：`MBR`和`Boot Sector`。
>
> `Linux`下`Ctrl+D`代表`End Of File`，`EOF`的意思，这个快捷键可以取代`exit`的功能，直接跳出文字界面。
>
> `Linux`命令行下按`Tab`键可以补齐命令，`man`和`info`命令可以查看`command`的帮助文档，`Ctrl+C`表示中断进程，`Ctrl+D`表示`EOF`特殊字符，`Ctrl+Z`表示挂起进程在后台运行。
>
> `Linux`系统下，用户和`root`相关信息记录在`/etc/passwd`下，个人密码则是记录在`/etc/shadow`下，所有的组名都记录在`/etc/group`内。
>
> `Linux`的权限不是很细致，拥有`rwx`三种：

```text
`r`（`Read`，读取）：   对文件而言，具有读取文件内容的权限；对目录来说，具有浏览目录的权限。

`w`（`Write`，写入）：  对文件而言，具有新增,修改,删除文件内容的权限；对目录来说，具有新建，删除，修改，移动目录内文件的权限。

`x`（`Execute`，执行）：对文件而言，具有执行文件的权限；对目录了来说该用户具有进入目录的权限。
```

> 可以用`chgrp`改变文件的用户组，`chown`改变文件的所有者，`chmod`改变文件的权限。
>
> `Linux`下文件的可删除和重命名权限是由其所在目录的`write`权限所决定的，要了解目录权限的意义。
>
> `Linux`下的文件类型：`-`代表常规文件，`d`代表目录，`l`代表链接，`b`（`block`）和`c`（`char`）代表设备文件，`s`代表`socket`文件，`p`代表`pipe`管道文件。
>
> `pwd`会显示出当前目录的路径，注意 `-P` 选项，如果当前目录只是以链接文件的形式存在，那么 `pwd -P` 就会显示出链接真正所指向的路径。
>
> `cp`命令：`cp -a souce dest` 相当于 `cp -pdr source dest`，完全复制目录的属性和档案，甚至是链接文件。如果不加任何参数的 `cp` 一个软链接，复制的结果会是源文件，而不是软链接，用 `-d` 可以解决，注意。
>
> 删除带有`-`开头的档案，例如 `-aaa` 这个文件，必须 `rm ./-aaa` 或 `rm -- -aaa` 才可以删除，否则`-aaa`会误判为参数。
>
> 查看二进制文件，有 `od` 和 `xxd` 命令，甚至有 `hexdump` 命令，都是以 `16`进制或`8`进制 显示输出，非常方便调试。
>
> 新建目录和档案的默认权限是由 `umask` 来控制的，一般我们在`linux`系统的 `umask` 设置为 `022` 比较好。
>
> `linux`下档案的隐藏属性：`chattr` 命令可以设置档案的隐藏属性，常用的有`i`属性（任何用户包括`root`都无法修改），`a`属性（只能增加数据，不能删除数据）等；`lsattr` 命令可以查看档案的隐藏属性，注意属性和权限是不同的，留个记性。
>
> `linux`文件的特殊权限：`SUID(u+s)`、`SGID(g+s)`和`SBIT(o+t)`。这三个特殊权限都是用来取代`x`权限的，所以设置这三个权限的前提条件就是必须具有`x`权限，否则小写的 `s`和`t` 权限就会变为大写的 `S`和`T` 权限，表示文件还不具备`x`权限，更谈不上这三个权限啦。
>
> `SUID(u+s)`仅能用在可执行的二进制程序上，目录无效。

```text
拥有`SUID`权限的二进制程序在执行时，执行者会暂时取得拥有者的权限，例如 `passwd` 命令就具有`SUID`权限，使得普通用户在执行 `passwd` 命令时会暂时 `root` 用户的权限，从而能修改`/etc/passwd`文件。
```

> `SGID(u+s)`不仅能用在可执行的二进制程序上，目录同样有效。

```text
拥有`SGID`权限的二进制程序在执行时，执行者会暂时取得该程序所属的群组支持，从而能访问自己群组本不能访问的文件；

拥有`SGID`权限的目录，一旦进入该目录，那么在目录下新建任何文件和目录，它们的群组都会与该目录相同，对于项目开发还是相当有用的。
```

> `SBIT(o+t)`仅能用在有`x`权限的目录上，文件档无效。

```text
拥有`SBIT`权限的目录，一旦进入该目录，当用户在该目录下新建档案和目录时，仅有自己和`root`才能删除该档案，即使文件具有`g+w`，`o+w`这样的属性，也会失效。例如`/tmp`就是这样一个文件夹。
```

> `SUID`权限为`4`，`SGID`权限为`2`，`SBIT`权限为`1`，因此可以用 `chmod 4755 file` 这样的命令来设置文件的特殊权限，还可以用 `u+s`，`g+s`，`o+t` 这样的设置法。
>
> `EXT2`文件系统的组成：最前面是一个`Boot Sector`，然后是`N`多个`Block Group`。
>
> 每个`Block Group`主要由`inodetable/datablock/superblock`等部分组成：

* `superblock`记录`Filesystem`的信息和`inode`、`block`的大小和数量等，一般在第一个`Block Group`里，后面的`Block Group`大部分都没有，有的话也只是第一个`Block Group`的备份；
* `filesystem description`主要记录`block group`的起始与结束的`block`号码，以及`group`每个区段分别介于哪一个`block`号码之间；
* `block bitmap`记录每个`block`号码是否使用中；
* `inode bitmap`记录每个`inode`号码是否使用中；
* `inode table`则是记录每个 `inode`（文件） 的权限、属性、容量等以及它真正内容所在的`block`号码；
* `data block`则是纯粹的数据记录。

> `Block Group`的基本单位是`block`，`block size`一般是`1K`、`2K`或`4K`。
>
> 每个文件只有一个`inode`，而每个`inode`可能指向多个数据相同的文件，每个`inode`大小一般`128`字节或`256`字节。
>
> 详细的`ext2`文件系统信息可以用 `tune2fs -l /dev/sda1` 或 `dumpe2fs /dev/sda1` 命令查看。
>
> 目录的链接数 包括目录本身、当前目录`.`和父目录`..`，每建立一个文件夹就多一个父目录`..`；文件的链接数指的是 该文件`inode`号的链接数，即是硬链接个数。
>
> `hdparm`命令可以用来测试硬盘读取速度，不过不是很准，`hdparm -Tt /dev/sda`。
>
> 在使用`fdisk`重新分区后，不要忘记使用`partprobe`命令让`kernel`更新分区表，很重要，否则系统可能会出错。
>
> `dd if=/dev/sda of=/dev/sdb`，这个命令可以让两个硬盘完全相同，因为`dd`可以读取硬盘的所有数据，包括`MBR`和`boot sector`等。
>
> `linux`启动时首先挂载临时根文件系统`initrd`（`Initial Ram Disk`），完成引导并挂载真正的根文件系统后再退出，不过在很多嵌入式设备中，它却是最终的根文件系统，因为它是文件系统的最小集合，非常适合嵌入式系统。
>
> `cpio`指令可以备份任何档案，包括`/dev`下的设备档案，正因如此，现在的`initrd`都是采用`cpio`备份再用`gzip`压缩生成的。
>
> `dos2unix`可以将`windows`文件的行尾字符`\r\n`转换成`unix`格式`\n`。
>
> `iconv`可以转换文件的字符编码，例如：`iconv -f gbk -t utf8 test.gbk -o test.utf8`。
>
> `ulimit`可以控制用户使用的系统资源，防止资源占用过高，系统崩溃。
>
> `env`是`shell`外置命令，可以显示当前`shell`的环境变量，又叫全局变量。`export`是`shell`内置命令，也可显示当前`shell`的环境变量。不过两者都另外有各自不同的功能，用法自己查吧。
>
> `set`是`shell`内置命令，可以显示包括环境变量、本地变量、内置变量、函数等所有`shell`设定值。不过它主要的功能是控制`shell`的内置设定，如`set -o`命令。
>
> `declare`也是`shell`内置命令，一样可以显示包括变量和函数等所有`shell`设定值。不过它主要的功能是声明变量和数组等值类型，`shell`内的变量包括字符串，整数，数组，只读，导出等不同的类型和属性，记得善加利用，会事半功倍哟。
>
> `bash`里面的各种变量操作，这可以节省我们的程序行数：

* `${str#pattern}`：从变量头部开始寻找符合`pattern`的数据，将符合的最短数据删除
* `${str##pattern}`：从变量头部开始寻找符合`pattern`的数据，将符合的最长数据删除
* `${str%pattern}`：从变量尾部开始寻找符合`pattern`的数据，将符合的最短数据删除
* `${str%%pattern}`：从变量尾部开始寻找符合`pattern`的数据，将符合的最长数据删除
* `${str/old/new}`：寻找变量内符合`old`的字符串，第一个符合的数据将被替换为`new`
* `${str//old/new}`：寻找变量内符合`old`的字符串，并将所有符合的数据替换为`new`

> 下面是变量赋值的各种替代操作，对于变量初始化很有用：

* `var=${str-expr}`：如果`str`没有设定，`var=expr`
* `var=${str:-expr}`：如果`str`没有设定或为空，`var=expr`
* `var=${str+expr}`：如果`str`有设定，`var=expr`
* `var=${str:+expr}`：如果`str`有设定且不为空，`var=expr`
* `var=${str=expr}`：如果`str`没有设定，`str=expr,var=expr`
* `var=${str:=expr}`：如果`str`没有设定或为空，`str=expr,var=expr`
* `var=${str?expr}`：如果`str`没有设定，`expr`输出至`stderr`
* `var=${str:?expr}`：如果`str`没有设定或为空，`expr`输出至`stderr`

> `history`可以查看最近下达的指令，而`!`则可以执行历史命令，如`!number`可以下达第`number`号指令，`!command`可以下达最近以`command`开头的指令，这就很有效率啦。
>
> `stty`可以控制终端的各种设定，如串口速率，快捷键等；此外还有`set`命令可以控制`bash`的各种功能设定；两者合作决定了我们的终端机。
>
> `bash`默认组合按键：

* `Ctrl+C`：终止当前命令
* `Ctrl+D`：输入结束符（`EOF`）
* `Ctrl+M`：输入回车符（`Enter`）
* `Ctrl+S`：暂停屏幕输出
* `Ctrl+Q`：恢复屏幕输出
* `Ctrl+U`：删除提示符整行命令
* `Ctrl+Z`：暂停目前的进程

> `bash`中的标准输入，标准输出，标准错误：

* `1>`或`>`：标准输出，覆盖形式
* `1>>`或`>>`：标准输出，追加形式
* `2>`：标准错误输出，覆盖形式
* `2>>`：标准错误输出，追加形式
* `<`：标准输入
* `<<`：标准输入的结束符（`EOF`）

> 对于追加的理解，我认为是输入或输出取代`EOF`的操作。
>
> `tee`命令可以在标准输出的同时，转存一份到文件内，这对于数据分析及存储非常有用。
>
> `tr`命令常用来删除特殊字符，或者对特殊字符进行转换，例如`TAB`符，`DOS`行尾符等都可以很轻松的转换和删除。
>
> `join`可以连接相关数据，要求是某字段必须相同，与`sort`一起使用可以用来连接数据生成表格哟；`paste`则相对简单，不需要数据相关，直接将两行贴在一起，并用`TAB`隔开，也很有用。
>
> `spilt`用来分割文件，可以指定文件以大小或行数来分割成`N`个小文件。
>
> 由于许多命令并不支持管道符，这里我们就可以使用`xargs`来调用不支持管道符的命令，它可以读取前面命令的输出作为参数提供给后面的命令来执行，这样就可以连接起不支持管道符的命令，用法很多。
>
> `printf`命令类似于`C`语言的`printf`函数，可以格式化输出，善加运用，打印字符串会很美观。
>
> `sed`的最小处理单位是行，对文本的行操作很有效率；而`awk`的最小处理单位是字段，对文本的列操作很有用，其命令格式如下：
>
> `awk 'pattern1{action1} pattern2{action2}...' file`
>
> 常用选项：

* `awk`的默认分割符是空格，可用内置变量`FS`指定；
* 内置变量`NF`：代表每一行（`$0`）的字段总数；
* 内置变量`NR`：代表`awk`目前正在处理的行数；
* `pattern`可以为空，常用的选项有`BEGIN`，`END`，条件判断和正则表达式等；
* 例如：`awk 'BEGIN{FS=":"} $3<10{print NR"\t"$1"\t"$3} END{print FS, NF, NR}' /etc/passwd`

> `diff`和`patch`常用于补丁的发布：生成补丁`diff -Naur dir1 dir2 > dir.patch`，更新补丁`patch -p0 < dir.patch`，还原补丁`patch -R -p0 < dir.patch`。
>
> `bash`中的`[[ ]]`比`[ ]`更加高级，判断条件更加厉害，它可以判断出`linux`通配符（`==`）和正则表达式（`=～`），还有`&&`，`||`和`!`等高级功能，善加运用，很厉害，具体参考`help [[`。
>
> `bash`的命令行参数默认用`$1 $2 ... $9`来表示，超过`10`个参数的话必须用到`shift`命令，`shift n`可以拿掉最前面的参数，使参数偏移`n`位，再次查看参数个数`$#`时就会发现参数少了，就可以继续使用后面的参数啦。
>
> 关于`shell`脚本的`debug`，我们可以使用`bash -x test.sh`来进行脚本的错误检查。
>
> `Linux`用于帐号管理的`ACL`需要文件系统的支持，并且`mount`选项里要有`acl`才行。然后就可以使用`setfacl`和`getfacl`来对文件和目录针对某一使用者的权限进行管理。
>
> 使用`su - user`来切换身份会更好，因为它是`login-shell`方式，会转化成新的用户环境，否则的话，虽然切换了身份，但环境变量还是当前用户的环境变量。
>
> `visudo`可以管理用户的`sudo`权限，不要直接修改`/etc/sudoers`文件，因为会有语法问题。另外`Linux`下的许多需要认证的命令（例如`passwd` `sudo` `su`等）都会用到`PAM`模块，这是一个专门用于认证授权的库，可以在`/etc/pam.d/*`中找到支持的命令或服务。
>
> `who`查看当前登入用户，`write`可以发送信息给用户，`mesg`让用户可以控制是否接受信息，`wall`则对所有用户进行广播信息。
>
> 手动建立用户帐号流程：

* 建立群组（`vi /etc/group`）
* 同步`/etc/group`到`/etc/gpasswd`（`grpconv`）
* 建立帐号（`vi /etc/passwd`）
* 同步`/etc/passwd`到`/etc/shadow`（`pwconv`）
* 建立帐号密码（`passwd user`）
* 建立主目录（`cp -a /etc/skel /home/user`）
* 更改主目录属性（`chown -R user:group /home/user`）

> 针对服务器的磁盘限额配置，我们可以使用`quota`来配置，它也需要文件系统的支持，记得`mount`选项加上`usrquota`和`grpquota`。
>
> `LVM`可以弹性调整文件系统的容量，并且拥有快照功能，作为虚拟机的文件系统很是有用。
>
> 在特定时间进行排程工作，我们可以使用`at`指令，而`batch`可以让`at`任务在`CPU`负载较小时才进行任务。
>
> 普通用户可以使用`crontab -e`来设定循环工作排程，而`ROOT`用户则可以直接编辑`/etc/crontab`来设置系统的循环排程。`anacron`可以在系统启动时唤醒停机期间未进行的`crontab`任务。
>
> `ps`可以截取当前系统的运行进程，`pstree`可以显示进程树，`top`可以实时监控运行进程，`vmstat`可以查看系统资源的使用情况。
>
> 熟悉几个`kill`信号的意义：`1 - SIGHUP`代表让程序重新读取配置文件；`9 - SIGKILL`代表强制中断一个程序；`15 - SIGTERM`代表以正常的结束方式来终止该程序。
>
> `nice`和`renice`可以调整程序的优先级高低，`PRI`值越低，程序就较优先被处理。
>
> `netstat`和`ss`这两个命令分属不同的网络工具包，均可以查看当前系统的网络连接状况，不过`ss`比`netstat`快多了。
>
> `fuser -uv /dev/pts/0`可以根据打开的`files`或`sockets`（这里是`/dev/pts/0`）找到运行的程序，而`lsof`可以列出被运行程序打开的所有文件，`pidof`可以找出运行程序的`PID`值。
>
> `Linux`内核自带有`SELinux`安全机制，不过`Ubuntu`默认没有安装，一般为了安全，服务器端会启动，其主要作用是保证主体程序（主要是网络服务）仅能存取指定文件档案资源，即使程序被攻破，也不至于让黑客获得更多的文件档案和用户权限。
>
> `Linux`服务程序可以分为两类：`Stand Alone`方式和`Super Daemon`方式。

* `Stand Alone`方式自己单独启动并常驻内存，例如`httpd`和`vsftpd`等；
* `Super Daemon`方式则是所有服务由`xinetd`统一管理，平时不启动，需要时才由`xinetd`调用启动，所以比较省内存，但反应比较慢；
* `/etc/services`里有所有服务的端口设置，`/etc/xinetd.d`则存放所有服务的配置文件，而`Super Daemon`的默认配置文件在`/etc/xinetd.conf`里。

> `rsync`是用来同步两台电脑文件夹的程序，对于服务器备份非常有用。
>
> `/etc/hosts.allow`和`/etc/hosts.deny`只对支持`TCP Wrappers`的程序才有用，可以用`ldd`来查看程序是否支持`TCP Wrappers`。 `CentOS`中的`chkconfig`可以进行系统启动服务的管理，而在`Ubuntu`中可以用`initctl`（`Upstart`服务在`/etc/init`）和`update-rc.d`（`SYSV`服务在`/etc/init.d`）来代替。
>
> `Linux`系统的`log`主要记录在`/var/log`下面，不过不同的发行版记录`log`的文件差异颇大，可以自行配置类似`/etc/rsyslog.conf`的文件，设定不同`log`的记录位置，甚至可以开启日志服务器。最后还要配置`/etc/logrotate.d/*`档案来设置`log`的备份周期，大小，个数，动作等参数，这样就可以周期备份和替换`log`文件，避免让`log`文件太大，影响系统效率。
>
> `Linux`早期通过`mknod`手动创建静态设备，不管设备是否被用到，这就需要在`/dev`下创建大量设备，但随着大量设备的出现，设备的动态检测和识别出现了问题，往往一个设备拔下再插入后设备名出现了变化，大量相同设备插入后识别困难，这对于开发者十分不便。自从内核`2.6`版本以后，出现了一种叫`sysfs`的新虚拟文件系统，它可以将内核支持的设备映射到`/sys`文件夹下，`udev`就是借此实现了用户空间（`user space`）的动态设备检测，创建和更新，这样系统启动时就可以动态创建设备，你还可以指定设备为特定名称，`udevd`后台服务将会为你自动更新设备。
>
> `Linux`系统开机流程：

* 按下`Power Button`，硬件逻辑电路完成`CPU Reset`，进入实地址模式，而其中`CS:IP=FFFF0H`，决定了`CPU`的第一条指令地址，就是跳转到`BIOS`首地址，于是`BIOS`就此启动；
* `BIOS`加载`CMOS`的硬件信息并进行开机自检；
* `BIOS`取得第一个开机装置，并读取执行`MBR`内的`Boot Loader`；
* `Boot Loader`依据设定加载`Kernel`，`Kernel`挂载根目录，检测硬件并加载驱动程序；
* 硬件驱动成功后，`Kernel`主动呼叫`init`程序，而`init`会取得`RUNLEVEL`；
* `init`执行`sysinit`完成系统环境初始化（如网络，时区等）；
* `init`依据`RUNLEVEL`启动各个服务（`/etc/init.d/rc $RUNLEVEL`）；
* `init`执行本地服务（`rc.local`）；
* `init`执行`getty`启动`login`程序，等待用户登录；

> `sysctl`可以在系统运行时读取和修改`kernel`的参数，你可以在`/etc/sysctl.conf`里做永久修改。
>
> `Ubuntu`中`telinit N`可以用来切换当前系统的`RUNLEVEL`，所以你可以用`telinit 0`来关机，`telinit 6`来重启。
>
> `Linux`内核模块常用命令：

* `depmod`会主动分析目前内核模块的相互依赖性，并重新生成`/lib/modules/$(uname -r)/modules.dep`，这个文件对于`modprobe`命令非常重要；
* `lsmod`可以列出目前内核加载的模块，`modinfo`可以查看某个内核模块的详细信息；
* `modprobe`可以根据`modules.dep`文件分析依赖性，然后安装和卸载内核模块，推荐使用；
* `insmod`和`rmmod`分别是安装和卸载模块命令，不过需要完整路径，也不会分析依赖性，适合完整无依赖，自己单独编写的模块，否则不推荐使用；

> 我们可以利用`Grub`救援`Linux`系统，进入`Grub`菜单，按`e`进入编辑模式，在`kernel`后加上`single`，`emergency`或`init=/bin/bash`等参数进入救援模式。
>
> `chroot`可以帮助我们切换根目录，改变运行环境，如果一个`Linux`硬盘出了问题，可以插到另一台`Linux`主机上，利用`chroot`命令切换到问题硬盘的`Linux`环境上来解决问题，好像一个便携式系统哟。
>
> `nc`是网络黑客利器，用处非常大，例如`nc -zv 127.0.0.1 631`可以扫描目标主机的`631`端口，还有好多好多功能，自己去看`man nc`吧。
>
> `Linux`预设的打印服务是`CUPS`，可以使用`http://localhost:631`来连接管理打印机，也可以使用`lp`系列指令来管理，不详述了，如果将`CUPS`设定为网络打印机服务器，其他人可以使用类似`ipp://192.168.1.10:631/printers/HP_Printer`的`URL`来连接。
>
> `Ubuntu`的软件管理命令：`dpkg`管理本地`deb`安装包；`apt`管理在线仓库的`deb`安装包；`add-apt-repository`可以增加或删除在线仓库。
>
> 对于`xft`字体，系统添加新字体后即可使用，`fc-list`查看可用字体，如果新字体没有显示，执行`fc-cache -v`更新字体缓存即可。
>
> `X Server`管理系统硬件，`X Client`则是应用程序，每个`X Client`都不知道对方的存在，必须通过`X Window Manager`来管理所有的`X Client`，`Ubuntu`使用`lightdm`来管理桌面窗口。
>
> `X Server`可以启动多个，使用`xinit`命令并指定`-display`选项即可，显示位置为`:0, :1 ...`；命令行模式下可以使用`startx`来启动桌面，不过并不会加载个人设置，使用有限制，推荐使用`sudo service lightdm restart`来启动桌面。
>
> `Linux Kernel`编译和管理命令：

* `make mrproper`彻底清除目标文件和配置文件；
* `make clean`清除编译过程产生的目标文件等，不会删除配置文件；
* `make menuconfig`生成内核配置文件；
* `make oldconfig`使用已经存在的`.config`作为默认值，只列出新功能选项，简化挑选过程；
* `make vmlinux`编译生成未压缩的内核；
* `make modules`仅编译内核模块；
* `make bzImage`编译生成压缩过的内核；
* `make all`等于`make vmlinux modules bzImage`（预设，同`make`）；
* `make modules_install`安装内核模块到`/lib/modules`；
* `make install`安装内核`bzImage`到`/boot`，生成`initrd.img`，并更新`grub`配置；

`Ubuntu`生成`initrd.img`的命令是`mkinitramfs`，查看`initrd.img`内容的命令是`lsinitramfs`，还可以用`update-initramfs`管理`/boot`下的`initrd.img`文件。
