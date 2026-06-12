---
title: "lvm adding new hard disk problem"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by fsman on 2005-12-06
I've got two hard disks and LVM configured.

First HD was configured with LVM at install time
/Ubuntu/root LVM
/Ubuntu/swap_1 LVM
/Ubuntu/home LVM

Then I did pvcreate /dev/hdb
lvextend -l 64855 /dev/Ubuntu/home             - extended home to scan both disks

then used the livecd using "resize2fs" to reallocate /home

Problem is I'm worried that I have done something wrong as I get the following error "Disk /dev/hdb doesn't contain a valid partition table" when I do

paul@Paul:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          31      248976   83  Linux
/dev/hda2              32       14593   116969265    5  Extended
/dev/hda5              32       14593   116969233+  8e  Linux LVM

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdb doesn't contain a valid partition table
paul@Paul:~$


Is everything OK?
Do I need to mount hdc somehome

I'm new to LVM and nervious (this is my second clean install with LVM)

---

