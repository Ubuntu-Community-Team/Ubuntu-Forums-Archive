---
title: "Karmic Install won't boot"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by WildeBeest on 2009-11-02
I have three hard drives in my system. One has a Hardy install, another has Win 7.
I installed Karmic on the other hard drive. There were no errors during the install process.

I selected custom partitions and selected the empty hard drive, set EXT3 file system and a mount point of /.

I can boot into Hardy and chain to Win7 or boot Win7 directly by setting the Boot priority in the Bios.

When I set the boot priority to the drive that has Karmic it just hangs, no error messages or anything.

Here's the fdisk -l listing:
```
Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c6c6c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2230    17912443+  83  Linux

Disk /dev/sdb: 36.9 GB, 36954402304 bytes
255 heads, 63 sectors/track, 4492 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6a2b0d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4302    34555783+  83  Linux
/dev/sdb2            4303        4492     1526175    5  Extended
/dev/sdb5            4303        4492     1526143+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd75011cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9730    78148608    7  HPFS/NTFS

```sda1 has the Karmic install.

How can I fix this?

---

### Post by WildeBeest on 2009-11-03
Bump
 
I little more info.
I can see the files on The Karmic install from Hardy.
 
Also the boot configuration file for Karmic has entries for Hardy and Win7.

---

### Post by WildeBeest on 2009-11-04
Anyone have any ideas?

---

### Post by antiram on 2009-11-04
if you are absolutly sure that sda is the right drive after changing something with boot in bios, make grub bootsector with:
grub-install /dev/sda

---

### Post by WildeBeest on 2009-11-05
100% sure.

Did not work.

---

