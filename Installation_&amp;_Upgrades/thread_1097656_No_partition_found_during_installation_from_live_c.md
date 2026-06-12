---
title: "No partition found during installation from live cd image"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by danielnpu on 2009-03-16
Hi,

I am booting xubuntu from a live CD image from my hard drive. The system is sucessfully brought up and everything works fine.

Then I decide to install the system to my hard disk. However the installation guide on desktop cannot find any partition information at step 4. So I cannot go ahead with the installation.

To my big surprise if I run GParted at the same time, it lists all my partitions successfully. Really strange. It looks like the partition tool of installation guide doesn't work well.

Could you please help with this issue? I've tried it many times, but was always blocked at the same place.

Here is the partition list showed by GParted:

/dev/sda1 fat32 mountpoint:/isodevice
/dev/sda2 extended
   /dev/sda5 fat32
   /dev/sda6 fat32
   /dev/sda8 linux-swap 258M
   /dev/sda9 ext3 6G
   /dev/sda10 ext2 4G
   /dev/sda7 fat32

All fat32 partitions are reserved for winXP.

Please help. Thanks a lot in advance.

Daniel

---

### Post by danielnpu on 2009-03-16
Can anyone help with this? Thanks!

---

