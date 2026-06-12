---
title: "ubuntu 9.04, not recognizing windows xp during installation"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by xviper on 2009-06-06
Hi,

I have installed previous versions of ubuntu, but never has it missed recognizing my windows installation. I'm trying installing ubuntu 9.04, but during partition stage of the installation, it's not showing the option of installing "side by side".

Instead it's saying that "No other operating system is found on this computer" Please help me on this, if I'm missing / doing anything wrong.

Here is the output of fdisk -l:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4895

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276        2319     8385930    f  W95 Ext'd (LBA)
/dev/sda3            2320        3564    10000462+  83  Linux
/dev/sda4            4501        4865     2931862+  82  Linux swap / Solaris
/dev/sda5            1276        2319     8385898+   b  W95 FAT32
/dev/sda6            2320        3564    10000431    7  HPFS/NTFS
/dev/sda7            3565        4500     7518388+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65a80794

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   42  SFS
```

As shown, I have two HDD, one with 40 GB (where I want both of the OS's) and the other is 160GB HDD. I previously had slackware on /dev/sda3, and my /home partition as /dev/sda7


>--Thanx--xviper--<

---

### Post by labinnsw on 2009-06-06
Did you use the manual option to partition?
Have you selected sdb instead of sda?

---

### Post by xviper on 2009-06-06
Yes, I have selected the manual partition, and no I selected sda, since I want ubuntu on my primary HDD

---

### Post by labinnsw on 2009-06-06
In that case, the only thing I can think of suggesting is to install 8.10 and do an upgrade to 9.04. First give this post some time though, see if anybody else can come up with a better solution.

---

### Post by presence1960 on 2009-06-06
which partition is windows installed on?

---

### Post by Mark Phelps on 2009-06-07
Had a similar problem with my machine using the standard desktop liveCD.  Booted using the alternate CD, and its partitioner saw my previous installations.  Suggest you try the alternate CD, or you could boot using a GParted LiveCD (which you can get from distrowatch.com), partition manually using that, and then boot from the desktop CD and see if it finds your newly formatted partitions.

---

