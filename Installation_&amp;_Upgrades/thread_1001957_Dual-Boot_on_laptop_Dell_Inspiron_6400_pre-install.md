---
title: "Dual-Boot on laptop Dell Inspiron 6400 pre-installed Ubuntu"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by jeanjean84 on 2008-12-04
Hello,
I need assistance to advise my oldest son (who lives in Africa: Liberia).
He has a laptop Dell Inspiron 6400 pre-installed with Ubuntu Feisty. 
He is very happy with it, but needs to have Windows XP for his on-line studiesâ€¦ 
Therefore dual-boot... Not too difficult! 
I have that at home and have the practice of the crashes at the time of Windows installation, reinstall of GRUB, etcâ€¦

The problem comes with the partitioning of these Dell laptops:
```
$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13         274     2104515    b  W95 FAT32
/dev/sda3   *         275         299      200812+  83  Linux
/dev/sda4             300        9729    75746475    f  W95 Ext'd (LBA)
/dev/sda5             300         379      642568+  82  Linux swap / Solaris
/dev/sda6             380        9729    75103843+  83  Linux

```
How to install XP in the simplest possible way?  

Personally I think that the simplest way would be:  

* to delete sda1 Dell Utility!  

* sda2 is the "Reinstall Operating System"... could be useful... but not abolutely necessary with the Ubuntu Live-CDs... but I would keep it though!  

* sda3 is the /boot: useful on a separated partition in multi-boot, isn't it?  (personnally, I do not have /boot on an independent partition, so I do not really know...)  

* sda4 : I would clean it ( delete the useless files, transfer the files not very often used on external disc or DVDs) and resize this extensive partition to 40 or 45 or 50 Gib).  

* I would then create a primary partition on the free space (30 or 25 or 20 Gib) for XP.  

With GParted, it is probably necessary to do it in several steps:  

1) deleting sda1.  

2) resizing the extensive partition sda4.  

3) creating the new primary partition at the end of the hard disk. I understand it will be called sda1.

Then installing XP on this new primary partition.  

It is a correct procedure?  

It will be necessary of course to fiddle with GRUB (or maybe not as /boot is on an independent partition?).  

Please help!  Advice needed! ;)

Bye for now! ):P

---

