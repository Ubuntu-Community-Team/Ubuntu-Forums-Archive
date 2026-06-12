---
title: "[SOLVED] Ubuntu can't see two HD"
date: 2008-10-14
forum: Hardware
---

### Post by username001 on 2008-10-14
I'm having a strange problem and I'm hoping someone can help me figure it out.  I have had ubuntu running on a 300 GB hard drive for a few months.  I just bought a 1 TB western digital caviar gp hard drive, which I would just like to use for storing data.  If I boot ubuntu from CD, I can see the new HD and format it.  However, if I plug in both HD at the same time, and boot from the old HD, I can't see the new HD in ubuntu, but I can see it in the bios.  The two HD seem to work fine individually, but not when plugged in a at the same time.  Thanks

---

### Post by username001 on 2008-10-14
Below is the output from sudo fdisk -l, which seems to show only the smaller HD.  Thanks.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000afe48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3825    30720000    7  HPFS/NTFS
/dev/sda2            3826       38658   279796072+  83  Linux
/dev/sda4           38659       38914     2048000   82  Linux swap / Solaris

---

### Post by username001 on 2008-10-30
The problem was with the power supply.

---

