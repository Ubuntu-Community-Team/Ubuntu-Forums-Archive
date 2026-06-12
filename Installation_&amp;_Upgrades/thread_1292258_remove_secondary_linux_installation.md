---
title: "remove secondary linux installation"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by ricklerre on 2009-10-15
Hey all,

I originally installed Ubuntu jaunty x86_64 side by side with Jaunty x86.  after playing with both for a while it's clear that for my purposes I need to be using 32-bit, and I'd like to remove and reclaim the space that the 64-bit installation is occupying.

My partition table has the following:
/dev/sda1: my / partition for 64-bit, has a boot flag, and is a primary partition
/dev/sda2: extended partition
  /dev/sda6: my / partition for 32-bit, no flags, logical partition
  /dev/sda7: swap space for 32
  /dev/sda5: swap space for 64

All the installation was done with mostly defaults in the ubuntu installer.  What do I need to do other than delete the partitions for 64-bit?

---

### Post by ajgreeny on 2009-10-15
Run your live CD, open Partition Editor and delete the 64 bit partitions, both of them as you do not need two swaps, and then just expand your 32 bit partition into the free space.  This will take a long time as the partition will have to be moved backwards on disk to do it, but it should work.  Make sure you have backed up first, just in case it all goes wrong.

I have just noticed that sda1 is a primary partition, the rest extended, so to expand sda6, you will first have to expand sda2 to fill the space, then sda6.  You may also need to restore or install grub from sda6 instraed of sda1 which will have gone, so before doing anything else, boot into your 32 bit system and run ```
sudo grub install /dev/sda
```which will change grub from the 64 bit to the 32 bit grub, if it is not already using that version's grub

---

### Post by ricklerre on 2009-10-16
the grub install needs to be done before deleting the partitions?

---

### Post by ajgreeny on 2009-10-17
> the grub install needs to be done before deleting the partitions? 	

Yes it does or there will be no grub configuration files for grub to read

---

