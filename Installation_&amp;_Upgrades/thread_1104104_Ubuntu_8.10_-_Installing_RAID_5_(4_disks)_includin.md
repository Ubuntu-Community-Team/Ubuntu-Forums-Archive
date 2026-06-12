---
title: "Ubuntu 8.10 - Installing RAID 5 (4 disks) including a disk in use"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by amazing mustard on 2009-03-23
Hello,

I have a GA-S68SM-S2 motherboard with four SATA 3 Gb ports. Currently I have one Maxtor Diamondmax 21 STM3500630AS 500 GB attached. It is in full use and has about 70 GB free space left. I bought 3 additional identical disks to set up a RAID 5 array using software RAID, in which I would like to include the disk in use.

My question:
Is it possible to keep my data while including this disk in a software RAID 5 array? I'd hate to install everything all over again.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00073e1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60075   482552406   83  Linux
/dev/sda2           60076       60801     5831595    5  Extended
/dev/sda5           60076       60801     5831563+  82  Linux swap / Solaris
```

---

### Post by Bachstelze on 2009-03-23
Yes.

Basically, you can temporarily set up your RAID with one missing drive. That will allow you to copy the data from that drive to the RAID, and then you can add the last drive to your array.

Normally, to build a 4-disk RAID-5 array, you would do:

```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

instead, do for example:

```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdd1 missing
```

---

