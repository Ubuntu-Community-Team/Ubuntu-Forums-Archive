---
title: "Partition help"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by ronbrooks on 2006-12-15
I am new to Linxu and need some help in setting up the partitions on my hard drive. I don't know why I have so many partitions on the drive but I want to delete some of them and make the others larger.  When I installed some of the up dates I got a pop up that said the drive was full. I do have a live CD and could someone walk me through how to set the drive up the right way. If you need more info let me know what you need and I will post it. 

My second drive look like it is set up ok. 

Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2329    18707661   83  Linux
/dev/hda2            3975        4870     7197120    5  Extended
/dev/hda3            2330        3450     9004432+  83  Linux
/dev/hda4            3451        3974     4209030   83  Linux
/dev/hda5            4684        4870     1502046   82  Linux swap / Solaris
/dev/hda6            4584        4683      803187   82  Linux swap / Solaris
/dev/hda7            4533        4583      409594+  82  Linux swap / Solaris
/dev/hda8   *        3975        4504     4257162   83  Linux
/dev/hda9            4505        4532      224878+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/hdb2            1217        3649    19543072+   f  W95 Ext'd (LBA)
/dev/hdb5            1217        2432     9767488+   b  W95 FAT32
/dev/hdb6            2433        3649     9775521    b  W95 FAT32

---

### Post by rlozano on 2006-12-15
do yo have plans of re-installing/re-formatting your machine?

---

### Post by Sef on 2006-12-15
I would delete the extended partition (/dev/hda2)  and reinstall the swap.  Swap should be double your ram.

You can use [GParted]("http://gparted.sourceforge.net/livecd.php") which is on the Live CD or you can download [GParted]("http://gparted.sourceforge.net/livecd.php") itself.

---

### Post by antar on 2006-12-15
> **Sef said:**
> 
You can use [GParted]("http://gparted.sourceforge.net/livecd.php") which is on the Live CD ...


Oh, HECK no! Don't ever, EVER trust the Ubuntu partitioner to do diddly-squat!

Yes, it's GParted, but it's an ANCIENT, buggy, buggy version.

Getting the Ubuntu partitioner to behave has consistently been the hardest problem I've had in installing Ubuntu (I've done it, now, five times on three computers).

Download the GParted LiveCD and run it by itself. GParted, I believe, is more reliable than the Norton $80 partitioning tool.

---

### Post by ronbrooks on 2006-12-15
I don't want to reinstall again if I don't have to but that is a thought.  I will have to down load all my programs again if I do. 

My question is why do I have four Linux swap file partition and three linux partition.  I guess what I am asking is what should I have.  Should I have just one swap partition and one Linux partition.  Would you recommend that I just start over and reinstall.  If I do start over how many partitions should I have.

---

