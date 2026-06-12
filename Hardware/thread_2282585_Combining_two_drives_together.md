---
title: "Combining two drives together"
date: 2015-06-15
forum: Hardware
---

### Post by matthew65536 on 2015-06-15
I have two flash drives, and i want to combine them together, much like you can do with RAID, but chromebooks don't have raid, so is there a software equivalent to raid? I have two Sandisk drives both 8GB. so what i want to do is combine them to make one big 16GB amount of space.

---

### Post by TheFu on 2015-06-15
If you ever move those devices to any other system, it is likely the data will be inaccessable.
There is SW-RAID.
There is LVM where you can combine multiple PVs into a single LV.
There are file systems like aufs which can make multiple partitions seem like 1 partition.
And, if you format with a Linux file system, you can also make use of symbolic links to make files on 1 partition appear like they are on another partitions.

Lots of optons.

However, flash memory is generally so slow that people don't use RAID or LVM with it. At least that is my guess for why they don't.

Chromebooks can run a full Linux and Linux definitely does have RAID.  I'm on a chromebook right now typing and it has LVM.

---

