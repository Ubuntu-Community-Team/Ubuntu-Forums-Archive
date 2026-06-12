---
title: "replace lvm disk from large filesystem spanning multiple disks"
date: 2014-01-12
forum: Hardware
---

### Post by fomember on 2014-01-12
I have a volume group with 3 disks of 2 TB.
The volume group holds one data volume with a 6TB file system.
One disk in this volume shows errors and I want to replace it.
The file system is filled with data of about 4.5 TB.

**What is the best way to replace one of my 2TB disks?**

I have found a lot of examples with pvmove and vgreduce but most do not deal with the file system.
From my understanding the advantage of LVM is that I can have a large file system spanning multiple physical drives.
Otherwise I could just as well use single drives and mount them together.
I know how to add another disk to the volume group.
But what are the steps to move the data off the faulty disk and put the new disk into the file system without losing any data?

---

