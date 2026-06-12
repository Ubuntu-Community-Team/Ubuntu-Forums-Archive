---
title: "[Help] I can't create any file or folder in Partition use NTFS"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by vietunion on 2007-06-30
Hello Everyone

First, sorry my english because i'm vietnamese

I have problem with ubuntu 7.04 and if you can, please help me ( im newbie )

My laptop ( Dell Inspiron 9200, Ram 512, CPU 1.6, HDD 40GB ), in HDD, i use PartitionMagic ( from HirenBoot CD ) to slip hdd to 4 partition

Partition 1: 15GB, use NTFS
Partition 2: 15GB, use NTFS
Partition 3: 9GB, use Ext3
Partition 4: 1GB, use  L-swap

I have setup Ubuntu 7.4 to partition3: 9GB ( Ext3 ) and use Partition4: 1GB for Swap, well, it's OK, almost Done

Start Ubuntu, open firefox, browse to ubuntuforums.org, it's run,  great :D
In Desktop, i can create file or folder, good

But when i go to sda1(15GB use NTFS ) and sda5(15GB use NTFS), i can't create folder or any file

I open Terminal and use this command

love@dhcppc2:/media/sda5 sudo mkdir test
Password: " i have type my password "

and this is error

"mkdir: cannot create directory 'test': Read-only file system"

Same problem with sda1

I use command ls -l

love@dhcppc2:/media$ ls -l
total 9
lrwxrwxrwx 1 root root       6 2007-06-30 02:19 cdrom -> cdrom0
drwxr-xr-x 2 root root    1024 2007-06-30 10:18 cdrom0
dr-xr-x--- 1 root plugdev 4096 2007-06-30 02:12 sda1
dr-xr-x--- 1 root plugdev 4096 2007-06-30 02:13 sda5



Please tell me how to create a file ( or folder ) in sda1 and sda5 ( i want use NTFS because i want install WinXP again - if ubuntu too difficult for me )

Please help me, thanks

---

### Post by longlegs on 2007-06-30
Hi,
You need to install and configure ntfs3g. Read 

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

for more information.
Good luck
longlegs

---

