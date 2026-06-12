---
title: "How Many Partitions"
date: 2010-06-14
forum: Hardware
---

### Post by BobbyDing on 2010-06-14
Hi Folks,
I have heard that there is a maximum of four primary partions. Is this per system? Or per drive? Also, are swap partitions considered primary?
 
At present I have three physical drives. One has XP to itself, one has Ubuntu to itself (with swap partition) and one is for Data. I am thinking of splitting the data drive and installing ubuntu studio onto one of those partitions.  Which will mean three partitions if you include the swap partition. Should this work OK? Anything I should look out for?
 
Thanks,
 
Bobby

---

### Post by Blackbird_13 on 2010-06-14
From [http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

The total data storage space of a PC hard disk is divided into at most four, and at least one, *primary partitions*. One of these can also be an *[extended partition]("http://en.wikipedia.org/wiki/Disk_partitioning#Extended_partition")*. 

An extended partition is a primary partition which contains *secondary partition(s)*. A hard disk may contain only one extended partition; which can then be sub-divided into *logical drives*.
.....
This means you can have lots of partitions as long as you have created an extended partition. I have the following on my second hard disc:

sdb1 boot (P)
sdb2 jaunty (P)
adb3 data (P)
sdb4 extended (E)
sdb5 tmp (L)
sdb6 swap (L)
sdb7 backup (L)

I use my first hard disc (sda) for windows and also to backup my ubuntu hard drive (sdb). There are plenty of guides on partitioning schemes - just google.

---

### Post by srs5694 on 2010-06-14
> **BobbyDing said:**
> Hi Folks,
I have heard that there is a maximum of four primary partions. Is this per system? Or per drive? Also, are swap partitions considered primary?

It's per hard disk, and what goes on the partition (filesystem, swap space, logical volume management, etc.) is irrelevant.

Also, note that this is a limit on *primary* partitions. You can use one of these four primary partition slots to create what's known as an *extended* partition, which can hold an arbitrary number of *logical* partitions. Linux is quite happy to reside entirely in logical partitions, and Windows can use logical partitions as data partitions.
 
> At present I have three physical drives. One has XP to itself, one has Ubuntu to itself (with swap partition) and one is for Data. I am thinking of splitting the data drive and installing ubuntu studio onto one of those partitions.  Which will mean three partitions if you include the swap partition. Should this work OK? Anything I should look out for?

Without knowing the exact partition layout, I can't be sure, but you'll probably be fine. If the partitioner gives you the option, I recommend installing Ubuntu entirely on logical partitions on the third disk, since this will minimize your use of primary partitions on the disk. Since some OSes, such as Windows and FreeBSD, require the use of a primary partition, you can run out of them in certain situations.

---

