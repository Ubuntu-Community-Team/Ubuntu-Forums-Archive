---
title: "accidentally zeroed hdd"
date: 2009-12-28
forum: Hardware
---

### Post by NewbuntuUser777 on 2009-12-28
I accidentally overwrote the first couple of mb of a hdd using dd.

The drive contained a single partition with ubuntu 9.04 plus a swap space.

I ran testdisk and it seemed to be able to find the swap but not the 
main partition.

Anybody know how to recover the drive contents (I used it to store all my 
important datas).

Thanks!

---

### Post by SecretCode on 2009-12-29
If you zeroed more than 32K then you overwrote the partition sector for the first partition, and that's why testdisk can't find the partition. 

There's a chance of recovering some of the data, but obviously you've also overwritten a bunch of directories and files.

Since you don't have other partitions to worry about, it might be possible to recreate the partition table and then run fsck and see what can be recovered.

How big is the drive and how much of it was used, roughly? If the data is really important you should probably make a raw clone backup of it before attempting recovery.

---

