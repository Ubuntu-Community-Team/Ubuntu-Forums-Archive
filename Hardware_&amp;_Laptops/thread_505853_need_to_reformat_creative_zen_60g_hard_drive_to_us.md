---
title: "need to reformat creative zen 60g hard drive to use as external drive"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by codebitch on 2007-07-20
Hi guys and girls a friend gave the hard drive out of a creative zen mp3 player and i was hoping to use it as an external drive I already have the enclosure for it. The proble is that it wont mount and or give me the ability to reformat it ive only been able to find it in the konsole it will list it when i do fdisk -1 and it tells me this

Disk /dev/sda: 60.0 GB, 60011642880 bytes
64 heads, 32 sectors/track, 57231 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

Disk /dev/sda doesn't contain a valid partition table

any help would be great and if you need more info let me know 

ciao
CB

---

### Post by yabbadabbadont on 2007-07-20
Remove all partitions (if any) and create a new one.
```
fdisk /dev/sda
```
Now put a filesystem on it.  Let's assume that you create an ext3 partition on the drive.
```
mke2fs -j -m 0 -L ZenDrive /dev/sda1
```
Enjoy.  :D

---

### Post by codebitch on 2007-07-20
thanks for the help yabadaba i created a new partition and tried to run the command you gave me to put a file system on it and got this 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
64 heads, 32 sectors/track, 57231 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       57231    58604528    5  Extended

Command (m for help):
seanpool@spikejr:~$ mke2fs -j -m 0 -L ZenDrive /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
[COLOR="Red"]/dev/sda1: Invalid argument passed to ext2 library while setting up superblock[/COLOR]

what did i do wrong?
 
CB

---

### Post by ubanchaos on 2007-07-21
same i got a 60 gig ipod and i wanna use my ipod and make it a hard drive is this possible

---

### Post by yabbadabbadont on 2007-07-22
```
/dev/sda1 1 57231 58604528 5 Extended
```
You created an extended partition....  Just create a single **primary** partition that is type 83 using fdisk.  (I think type 83 is the default for primary partitions created using Linux's fdisk)  Then you will be able to format it with the command that I gave you.  :)

---

### Post by codebitch on 2007-07-23
awsome I got it to work (I Cheated and used Qtparted) Thanks for all the help yaba. Now the problem is that it will only work on my linux machine and I would like it to work on both**[COLOR="SeaGreen"] linux [/COLOR]**and the _[COLOR="Red"]evil ones[/COLOR]_ OS Im just guessing but is it the ext3 file system I tried switching to fat32 since thats the only one i know works in windows but then it only said the free space was something like 28gb and then I rembered someone telling me that fat32 only worked up to that or somewhere there abouts. Any help would be great 

CB

---

### Post by yabbadabbadont on 2007-07-24
There are a couple of options for accessing an ext2/3 partition/drive from windows.  There is a file manager called Explore2fs and windows device drivers exist as well.  I have found two different device drivers and I know that I have used one of them successfully in the past, but I don't remember which one...  :?  You'll have to look them over and decide if you want to try either one.

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

---

