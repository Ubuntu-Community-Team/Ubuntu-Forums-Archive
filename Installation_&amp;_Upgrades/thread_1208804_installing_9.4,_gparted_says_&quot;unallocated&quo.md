---
title: "installing 9.4, gparted says &quot;unallocated&quot;, wrong!"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Lesconrads on 2009-07-09
Gentlemen, I have a problem installing a third OS on my Dell vostro 1500.

Gparted says, that my whole internal HDD is unallocated - which is WRONG. 
My external HDD with the backup gets shown correctly. One big ntfs thingie like I created it with. 

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2          240975    21205799    10482412+   7  HPFS/NTFS
/dev/sda3   *    21205800   281667644   130230922+   7  HPFS/NTFS
/dev/sda4       281667769   312578047    15455139+   f  W95 Ext'd (LBA)
/dev/sda5       307337216   312578047     2620416   dd  Unknown
/dev/sda6       281667771   301475789     9904009+  83  Linux
/dev/sda7       301475853   307323449     2923798+  82  Linux swap / Solaris

```You can see: I have a recovery partition, a dell media thingamajig, my Vista-installation and on the (ahm...) extended partition Ubuntu 8.10 and the ubuntu swap. 

My goal is to get some 10 gb of my Vista partition, move it to the extended part and get 9.4 running for testing purposes (and having a working ubuntu whilest getting 9.4 to work).

Why is gparted - in the installer aswell as in this live-cd I am using currently ASWELL as in my working ubuntu 8.10 showing wrong partition information? In every case, I can mount the partitions! 

Thanks a lot for any input
Les!

---

### Post by Mark Phelps on 2009-07-10
OK, couple of things ...

First, do NOT use GParted or any other Linux utility to shrink your Vista partition; instead use the Vista Disk Management utility.  If you do otherwise, you run the risk of corrupting the Vista OS partition, which can then only be fixed by booting from a Vista DVD and running Startup Repair repeatedly until it finds no more problems.

Second, there seem to be continuing problems with the desktop LiveCd version of GParted detecting some installations properly.  Suggest you do the following: either download and burn a GParted LiveCD (from distrowatch.com) and use that to create the Linux partitions, or download and burn the Alternate CD, and use it.

---

