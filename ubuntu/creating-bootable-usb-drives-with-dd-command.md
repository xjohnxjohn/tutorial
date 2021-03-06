# 使用dd命令创建可引导的USB驱动器

## 环境

- 操作系统：Ubuntu
- 系统版本：16.04.3 LTS

## 操作步骤

1. 打开终端，确认U盘路径：`sudo fdisk -l`；
2. 取消挂载U盘：`sudo umount /dev/sdb`（/dev/sdb是我的U盘设备）；
3. 格式化U盘：`sudo mkfs.vfat /dev/sdb -I`；
4. 将系统镜像写入U盘：`sudo dd if=xxx.iso of=/dev/sdb`（执行此命令时，终端不会有任何反馈，此过程会持续10分钟左右，当看到终端命令窗口有返回消息即制作完成）；

## [附]dd命令

用指定大小的块拷贝一个文件，并在拷贝的同时进行指定的转换。

#### 参数

- if=文件名：输入文件名，缺省为标准输入。即指定源文件。< if=input file > 
- of=文件名：输出文件名，缺省为标准输出。即指定目的文件。< of=output file > 
- ibs=bytes：一次读入bytes个字节，即指定一个块大小为bytes个字节。 
- obs=bytes：一次输出bytes个字节，即指定一个块大小为bytes个字节。 
- bs=bytes：同时设置读入/输出的块大小为bytes个字节。 
- cbs=bytes：一次转换bytes个字节，即指定转换缓冲区大小。 
- skip=blocks：从输入文件开头跳过blocks个块后再开始复制。 
- seek=blocks：从输出文件开头跳过blocks个块后再开始复制。 
- count=blocks：仅拷贝blocks个块，块大小等于ibs指定的字节数。 
- conv=conversion：用指定的参数转换文件。 
- ascii：转换ebcdic为ascii。
- ebcdic：转换ascii为ebcdic。
- ibm：转换ascii为alternate ebcdic。
- block：把每一行转换为长度为cbs，不足部分用空格填充。
- unblock：使每一行的长度都为cbs，不足部分用空格填充。
- lcase：把大写字符转换为小写字符。
- ucase：把小写字符转换为大写字符。
- swab：交换输入的每对字节。
- noerror：出错时不停止。
- notrunc：不截短输出文件。
- sync：将每个输入块填充到ibs个字节，不足部分用空（NUL）字符补齐。 
