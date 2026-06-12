---
title: "Help defining root system"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by wolfman1221 on 2009-02-21
I am trying to define  the root system for ubuntu.  I loaded ubuntu to the live desktop and I am currently on the partition editor. I have three partitions that look like this. 


/dev/sda1     ntfs  109.79 mib          

/dev/sda2     ntfs  iso device  55.78 GIB    used: 54.51 GIB  unused: 1.26 GIB   boot



unallocated 784 MIB 



If someone could help me, I would really appreciate it.

---

### Post by dstew on 2009-02-21
I assume you have a Windows system on that disk that you want to preserve, and dual-boot Windows and Ubuntu. You will need to create two new partitions for your Ubuntu installation. It looks like you can shrink the /dev/sda2 partition, and then create the new partitions out of the space you free up. You should create at least one 10 Gb partition for the Ubuntu root file system, and a 1 Gb swap partition.

To shrink the /dev/sda2 partition, if you have Windows XP, you defragment first using the Windows defragmentation tool, and then use the Ubuntu partitioner to shrink it down by say 12 Gb. If you have Windows Vista, you should probably use the Vista partition management software to shrink. After shrinking, you will have 12 Gb unallocated space, which you can use to create a 11 Gb partition, format ext3, and mount point '/' for the root partition, and 1 Gb partition "use as swap" (no format, no mount point for a swap partition).

I find it easier to partition before installing, using GParted from an Ubuntu Live CD system, or using a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php"). Then, when installing, the partitions are already there, and it is less anxiety provoking.

---

### Post by cariboo on 2009-02-21
You're going to need a lot more free space on the hard drive, if you want to install Ubuntu. My full installation of Jaunty takes up 3.6Gb on my / partition.

Jim

---

