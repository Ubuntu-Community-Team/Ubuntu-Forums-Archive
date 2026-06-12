---
title: "help: Need to partition the disk in which linux is installed"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by shajip88 on 2009-08-23
hi  my friend has one hard disk in which 2 partitions are made.

C: Ubuntu
D: Windows

The problem is he had installed ubuntu in 100Gb partitioned space and he cant see that in windows. So is there any way to partion the drive in which ubuntu is installed in 2  and without affecting both the os?

---

### Post by nhanquy on 2009-08-23
> **shajip88 said:**
> hi  my friend has one hard disk in which 2 partitions are made.

C: Ubuntu
D: Windows

The problem is he had installed ubuntu in 100Gb partitioned space and he cant see that in windows. So is there any way to partion the drive in which ubuntu is installed in 2  and without affecting both the os?

I don't completely understand your question at all.
First, C: D: drives are the DOS/Windows concept not Unix concept.
In general, a disk drive can be divided into many partitions (up to 4 primary). Also a concept of extended partition you should be familiar with. Extended partition could be considered as a disk drive inside a disk drive. The Extended partition can be divided with more partitions inside it.
From your post, I guess that both OSes working (?) and you want to shrink the partition Ubuntu resides.
If that was the case; then boot Linux from LiveCD; use Partition Editor to shrink (resize) the Ubuntu partition
to make some space.

---

### Post by Mark Phelps on 2009-08-23
> **shajip88 said:**
> hi  my friend has one hard disk in which 2 partitions are made.

C: Ubuntu
D: Windows

The problem is he had installed ubuntu in 100Gb partitioned space and he cant see that in windows. So is there any way to partion the drive in which ubuntu is installed in 2  and without affecting both the os?

You can't see that in MS Windows because it's not able to read Linux-formatted partitions.

Also, Linux doesn't use drive letters, so what tool are you using to see the partitions?

---

### Post by shajip88 on 2009-08-23
Ok there are 2 partitions in which ubuntu and windows are installed in each  partitions. Now i want to shrink ubuntu partitions from 100gb to 30gb and change the remaining 70gb to ntfs so that i can use in windows. Both os are working fine

---

### Post by stlsaint on 2009-08-23
boot to the livecd... alright with as big a resize that you are doing i recommend you format ubuntu completely then resize down to 30gb...you can use the simple backup suite in ubuntu repos to backup your /home and anything else you need...after the resize format the 70gb unallocated space to ntfs( also you could format the unallocated space as fat32 so both ubuntu and windows can share the drive together) but that may be a little more advanced so be careful!! now should you choose to put that 70gb back onto the xp partition than you will need to format the xp partition as well...then add the 70gb to the xp partition...ALL THIS CAN BE DONE USING THE LIVECD AND THE PARTITION EDITOR IN system>admin?partition editor!!!

---

### Post by shajip88 on 2009-08-24
thank u :) i ll try

---

