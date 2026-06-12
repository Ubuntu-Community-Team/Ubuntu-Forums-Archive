---
title: "external drive, partition, backuping and changeing owner privileges..."
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by Anguilla on 2005-04-21
hello I'm caming from fedora core3... and I'm a poor newbie...
before leaving redhat fc3 I made as a user said to me

```
rsync -r /home/my folder/ /media/my external harddrive/
``` 

Before I had done some partition on my firewire external hard disk
by fdisk and after using the command mkfs (to format with different file system), now I have the 2 partitions 100gb vfat32 mounted (automaticaly by the sistem) as normal user file system (under /media/...)
and the other 2 ext3 partition (20 gb and 30gb) mounted as root file system always in /media/... 

what I want to ask is that, now the result of rsync is under a ext3 partition (root owner) and I want to restore evolution and firefox datas (as normal user owner), so:
**1)was correct to use rsync?? **
**how can I copy that files back to get my email anf other config stuffs if now the  files are root files???** 
**why the system mount automaticaly the sda drive, with 2 partition with the privileges of normal user and the other 2 with root as owner??? how can I change it??**  

thank for the help

I made a mistake i'm using the ubuntu 5 version...

---

