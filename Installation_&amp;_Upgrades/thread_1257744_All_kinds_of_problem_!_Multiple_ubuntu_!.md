---
title: "All kinds of problem ! Multiple ubuntu !"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by prodigyaj on 2009-09-04
I had given less space in my root partition and hence wanted to increase. In my attempt I ended up screwing the entire partition !!! 
Now I have 93GB  unallocated in windows and and having multiple ubuntus in it.
Please guide me on how to format the everything apart from sda1and sda 6 (both are accesible from windows , basically i had c: d: e: and c: and e: still accesible from windows. I just want to format this d: and install ubuntu again allocating the entire d: to ubuntu !! 
heres the image as shown in gparted
[http://img40.imageshack.us/img40/7525/screenshotdy.png](http://img40.imageshack.us/img40/7525/screenshotdy.png)

AJ

---

### Post by Partyboi2 on 2009-09-04
Hi, you can boot a Ubuntu live cd and open gparted (System>Admin>Partition Editor) and right click on the swap partitions and choose to turn swap off, then delete the 3 swaps and 4 ext3 partitions, then install Ubuntu again using the newly create unallocated space.

---

### Post by presence1960 on 2009-09-04
> **Partyboi2 said:**
> Hi, you can boot a Ubuntu live cd and open gparted (System>Admin>Partition Editor) and right click on the swap partitions and choose to turn swap off, then delete the 3 swaps and 4 ext3 partitions, then install Ubuntu again using the newly create unallocated space.

+1

Do not use windows to do partitioning. The only exception is Vista and only for shrinking Vista's partition due to a known unresolved bug. Use the Ubuntu live Cd or gparted Live Cd to partition your disk.

I know you are new to Ubuntu so here is a heads up which will avoid confusion. Linux does not label disks & partitions as windows does. The C:, D:, E:, etc does not apply in Linux. refer to your photo you posted for our reference. Disks are labeled as sda, sdb, sdc, etc. partitions are labeled as sda1, sda2, sda3, etc. Please use this terminology when asking for help so we all are on the same page. E: on windows could be on a different hard disk than C: if you have more than one disk. But E; itself will not reveal that info. But with the Linux labels we will know immediately the partition's location.

---

