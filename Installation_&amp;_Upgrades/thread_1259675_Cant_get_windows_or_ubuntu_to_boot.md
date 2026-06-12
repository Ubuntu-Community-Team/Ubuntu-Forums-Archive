---
title: "Cant get windows or ubuntu to boot"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by w00ly on 2009-09-06
Hi all. I'm trying to setup a dual boot with XP and ubuntu. I already had ubuntu installed on it's own ext4 partitions and I had an existing NTFS partition from when I had windows before. I tried to setup XP in that partition but after the initial text-based screen where it copies all the files then reboots, it doesnt continue the installation. 

In the live cd I can mount the the partition and view the files but gparted only shows one large partition (mounted or unmounted) "unallocated" and wont give me the option to resize (only create new partitions). Since I dont want to overwrite existing data on the partition, how should I create a new partition in the free space for windows? Or how do I continue this stupid XP installation so I can eventually recover grub and get a dual boot working? Thanks in advance!

```
ubuntu@ubuntu:~$ fdisk -l

Disk /dev/sdb: 2032 MB, 2032664576 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x00049dbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         513      999984+   b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logical endings:
     phys=(124, 126, 3) logical=(512, 2, 5)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             513        1017      985023+  83  Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(124, 126, 4) logical=(512, 2, 6)
Partition 2 has different physical/logical endings:
     phys=(247, 31, 40) logical=(1016, 25, 2)
Partition 2 does not end on cylinder boundary.
```

---

### Post by presence1960 on 2009-09-06
that output you posted shows no linux partitions and a messed up partition table. The disk is barely 2 GB! What is up with that?? I thought you had Ubuntu installed?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

