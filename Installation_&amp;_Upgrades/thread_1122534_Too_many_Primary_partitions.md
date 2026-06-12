---
title: "Too many Primary partitions"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by oman.ispace on 2009-04-11
[SIZE=2]Hello All, ):P

[FONT=Verdana]
I am trying to install Ubuntu in my laptop side by side with Windows XP. However the when I try to install it on the free space in the harddisk (25 GB), the automatic partitioner complains about to many Primary Partitions in disk. I just wanted to know what is the best way to split the harddisk if I want both systems in the harddisk.[/FONT][/SIZE]

---

### Post by Partyboi2 on 2009-04-11
Hi, you can only have 4 primary partitions so you will need to create a extended partition which then will allow you to have as many logical partitions as you want.
You can use gparted (System>Admin>Partition Editor) on the ubuntu live cd to create the partitions before installing ubuntu. You will need a /swap partition (approx. 1.5x the amount of inboard ram) and a ext3 partition (remainder of allocated space for ubuntu)  Then choose the manual option for partitioning when installing and set the mount point for the ext3 to /

---

### Post by oman.ispace on 2009-04-11
> **Partyboi2 said:**
> Hi, you can only have 4 primary partitions so you will need to create a extended partition which then will allow you to have as many logical partitions as you want.
You can use gparted (System>Admin>Partition Editor) on the ubuntu live cd to create the partitions before installing ubuntu. You will need a /swap partition (approx. 1.5x the amount of inboard ram) and a ext3 partition (remainder of allocated space for ubuntu)  Then choose the manual option for partitioning when installing and set the mount point for the ext3 to /

So do I put Ubuntu in the extended partition or in a primary partition on its own.

Thanks

---

### Post by dandnsmith on 2009-04-11
It will live quite happily in a logical partition inside an extended partition.

It sounds as if there may be something further to be aware of - the extended partition counts as a primary partition, and I suspect there are already 4 primary partitions (in which case you'd have to back one up, delete it, and put the data into a logical partition in the extended partition - when you've created it).

---

### Post by oman.ispace on 2009-04-11
> **dandnsmith said:**
> It will live quite happily in a logical partition inside an extended partition.

It sounds as if there may be something further to be aware of - the extended partition counts as a primary partition, and I suspect there are already 4 primary partitions (in which case you'd have to back one up, delete it, and put the data into a logical partition in the extended partition - when you've created it).

I already have 3 primary partions in the hard disk. And I was not able to create an extended one in the free part of the disk.
:rolleyes:

Anyway I am backing up the important stuff becuase I will do a clean install of both systems 

:popcorn:

---

### Post by dandnsmith on 2009-04-11
If you only have just the 3 primary partitions, and you had a problem, then you do indeed need to use something like gparted to create the extended partition, and then you can have the linux main partition and the swap inside that.

My experience suggests that trying to do the partition bit, and then backtracking inside the ubuntu install can give a problem - its better to abandon the install, and start it again.

---

### Post by Partyboi2 on 2009-04-11
> **oman.ispace said:**
> I already have 3 primary partions in the hard disk. And I was not able to create an extended one in the free part of the disk.
:rolleyes:

Anyway I am backing up the important stuff becuase I will do a clean install of both systems 

:popcorn:
You would install ubuntu on the logical partitions. Make sure before working on the partitions that they are unmounted first. You can right click on them in gparted and choose to unmount.

---

