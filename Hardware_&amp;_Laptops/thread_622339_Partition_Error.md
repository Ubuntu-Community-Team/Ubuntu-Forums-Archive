---
title: "Partition Error"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by earendil1234 on 2007-11-24
I have my harddrive partitioned into two sectors, one for Windows XP and the other is for Ubuntu using partition magic. I wanted to resize my Windows Partition so as to create a partition for the data.

Last night, I used partition magic to resize my harddrive and when it was finishing (at 99%) it says that there is a corruption or something like that, and now it fails to read the rest of my harddrive. The good thing is that it is still able to read my partition for Linux. I tried to turn it on using safe mode..but it doesn't work..

Can I undo the partitioning? Because even Linux cannot recognize that part of my harddrive anymore...

Anyone can help? *desperate*

My laptop is Toshiba Tecra M3, 512 MB RAM, 60 GB harddrive if it ever helps...

---

### Post by Aniongap on 2007-11-27
Oh man. Partition magic, not looking at what kind of file systems can read, is used only for windows partitionig. Resizing partitions that uses primary logical drive, can cause problems like yours.

For futre partitioning, You better use fdisk for winz or cfdisk for linux systems. Linux partition tools are the better ones. You may not be use a gui mode, or shrink partitions virtually, but you will get better success.

It  is better always to burn one or few dvd's more to backup your data before changing something in disks.

Theoretically partition magic creates a snapshot of exist partition, to enable the posibility of undo changes. But only theoretically...
Practice is different.

I think your data is lost.:(

---

