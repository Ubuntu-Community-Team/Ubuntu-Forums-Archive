---
title: "Removing Windows partitions, and re-integrating them into Linux"
date: 2008-09-18
forum: General Help
---

### Post by liquidcross on 2008-09-18
I've got a Thinkpad R60 that triple-boots into either Ubuntu 8.04 (default), Windows XP Pro, or Windows Server 2003. I'm thinking of installing VMWare Workstation into Ubuntu, and running VMs of Windows within it. If I do so, I really won't need the other two Windows partitions anymore (I just use them for testing, and VMware will suffice). Is there any way to format them and merge them back with the Linux partition without reformatting and reinstalling the entire system?

---

### Post by vanadium on 2008-09-18
In principle, it comes down to deleting these partitions, then enlarge existing partitions to fill the free space or create a new partition to fill the free space. What you effectively can do depends on your current partitioning scheme. You could post it here if you want furhter thoughts: it is the output of 

sudo fdisk -l

---

### Post by liquidcross on 2008-09-22
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20971408+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2611        9069    51875271+   f  W95 Ext'd (LBA)
/dev/sda3            9070        9729     5299560   12  Compaq diagnostics
Partition 3 does not end on cylinder boundary.
/dev/sda5            2611        3917    10485688+   7  HPFS/NTFS
/dev/sda6            3918        4109     1542208+  82  Linux swap / Solaris
/dev/sda7            4110        9069    39841168+  83  Linux

---

### Post by vanadium on 2008-09-23
The only thing you could do easily with your current setup is:

* delete sda1 and sda2, create one new partition in that space
* reformat sda5 to ext3.

This would leave you with one system partition and two data partitions for Ubuntu. That is the only rearrangement that is easy to achieve.

You could also remove sda5 then move sda5 to that location, and finally expand sda6 to fill the remaining space. However, in this case you would need to move. While this is theoretically possible, it is a very slow proces, and although I never did this myself, everything I heard about it indicates that it usually does not work.

Other theoretical possibilities are to copy sda6 bit by bit to sda1, then delete the extended partition, etc. but also that will be slow and you need to know very well what you do. I definitely would go for repartitioning and a fresh install in this case.

---

