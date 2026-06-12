---
title: "Partitioning question"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Grimnir512 on 2008-12-30
OK, so it's not often I need help with partitioning but here I go:

I got a Dell Studio 15 for christmas and I plan to install Ubuntu on it. The only problem is that, when I was at the partitioning stage of the installer, I discovered I had three partitions there already:

A small one, the main (Vista) partition and a 10gb recovery partition.

What I am really wondering is if it is OK to delete the recovery and small partition and then resize my main partition to make way for Ubuntu, as if I remember correctly you can only have 4 primary partitions (or am I completely wrong?) and I plan on having three for Ubuntu (/, /home, and swap space), bringing me to six.

Will this stop me from being able to fix my Vista installation should it break? Or maybe better put, does my recovery CD need the recovery partition to work?

---

### Post by oilchangeguy on 2008-12-30
"Or maybe better put does my recovery CD need the recovery partition to work?" this makes no sense. edit your post. and NEVER, NEVER delete the restore partition. and find out what is in the small partition also. 

ah, i read it again, and it makes sense (NEEDS A COMMA). no the recoovery partition does not need the cd to work. but what if the cd is damaged, or misplaced? and you've deleted the restore partition?

---

### Post by Grimnir512 on 2008-12-30
> **oilchangeguy said:**
> "Or maybe better put does my recovery CD need the recovery partition to work?" this makes no sense. edit your post. and NEVER, NEVER delete the restore partition. and find out what is in the small partition also. 

ah, i read it again, and it makes sense (NEEDS A COMMA). no the recoovery partition does not need the cd to work. but what if the cd is damaged, or misplaced? and you've deleted the restore partition?

OK, so don't delete the restore partition. But what about the other small one?

---

### Post by SuperSonic4 on 2008-12-30
Best not to. You can have any number of extended/logical partitions and Linux boots perfectly from one of these

---

### Post by Grimnir512 on 2008-12-30
> **SuperSonic4 said:**
> Best not to. You can have any number of extended/logical partitions and Linux boots perfectly from one of these

OK :) Just out of interest, do you have any idea what it is for? This is the output from fdisk -l on my LiveCD:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          18      144553+  de  Dell Utility
/dev/sda2              19        1324    10485760    7  HPFS/NTFS
/dev/sda3   *        1324       30402   233566208    7  HPFS/NTFS

It's the one identified as Dell Utility, I think.

Edit: I think it may be this: [http://www.goodells.net/dellutility/index.htm](http://www.goodells.net/dellutility/index.htm)

I'll look into it. Thanks for the help all :)

---

