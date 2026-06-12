---
title: "Lacie 500 GB hard drive on Ubuntu Jaunty"
date: 2009-09-02
forum: Hardware
---

### Post by jqke on 2009-09-02
I just bought a 500GB external hard drive and I'm not having much luck finding a set up guide for Ubuntu.

The disk is mounted and shows on my desktop, however when I right click on the icon for the drive and go into the properties, it shows available space as 10MB.

It attaches through USB 2.0.

---

### Post by Whiffle on 2009-09-02
Interesting.  I have that exact drive...


Could you open up the terminal and run "sudo fdisk -l" with the drive plugged in, then post the output here?

---

### Post by jqke on 2009-09-02
Yep:

tobin@ubuntu:~$ sudo fdisk -l
[sudo] password for tobin: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc22c7adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       36862   294549500    7  HPFS/NTFS
/dev/sda3           36862       37906     8388608    f  W95 Ext'd (LBA)
/dev/sda4           37906       38914     8095744   17  Hidden HPFS/NTFS
/dev/sda5           36862       37906     8387584    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24796452

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              27          28       10239    c  W95 FAT32 (LBA)
tobin@ubuntu:~$

---

### Post by Whiffle on 2009-09-02
> **jqke said:**
> Yep:

tobin@ubuntu:~$ sudo fdisk -l
[sudo] password for tobin: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc22c7adf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
/dev/sda2   *         192       36862   294549500    7  HPFS/NTFS
/dev/sda3           36862       37906     8388608    f  W95 Ext'd (LBA)
/dev/sda4           37906       38914     8095744   17  Hidden HPFS/NTFS
/dev/sda5           36862       37906     8387584    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24796452

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              27          28       10239    c  W95 FAT32 (LBA)
tobin@ubuntu:~$

Looks like the drive is formatted incorrectly.  Start should be something near 1, and end should be near 60801.  I would repartition and reformat it...

---

### Post by jqke on 2009-09-02
How do I go about doing so?

---

### Post by Whiffle on 2009-09-02
I think the most common way to do it on Linux is to use gparted, which is available through Synaptic and will show up under System > Administration > Partition Editor .  Run it, select the drive you want at the top right corner( in your case /dev/sdb, be sure to double check it is indeed the drive you want ), and then click on the partition, delete it, then add a new one, and format it as FAT32.  Hit apply and it should work.  Then unmount/remove it, plug it back in, and you should be good to go.

---

### Post by jqke on 2009-09-02
Looking at GParted, I can see that a majority of the hard drive (465 GB) is 'unallocated' under file system. When I attempt to create a new partition it tells me


 There cannot be more than one primary partition. If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first.

---

### Post by Whiffle on 2009-09-02
You should delete any partitions that are already there, so that the entire drive is Unallocated, then try to add a new primary partition.  And if thats not it...then..HMM.

---

### Post by jqke on 2009-09-03
That worked, thank you!

---

