---
title: "Encryption and RAID: Safe? Stable? Recommended?"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by lightnb on 2009-05-24
I have two identical physical hard drives, each one partitioned into three sections.

Then, I created three software raid 1 (mirror) devices, that grouped each of those matching sections into arrays.

Then I made one array the /boot partition.

With the other two, I turned them into encrypted drives. One for root, the other swap.

The system does actually boot, but I find the message "Disk /dev/md1 doesn't contain a valid partition table" in the output of "fdisk -l".

Is that anything to worry about?

Will the virtual encryption drive on the raid array cause problems with replacement or damaged raid disks later on?

Is this a supported/recommend way to get drives that are encrypted AND on RAID 1?

**fdisk -l**:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003af27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sda2           60559       60801     1951897+  fd  Linux raid autodetect
/dev/sda3              25       60558   486239355   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003d17f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          24      192748+  fd  Linux raid autodetect
/dev/sdb2           60559       60801     1951897+  fd  Linux raid autodetect
/dev/sdb3              25       60558   486239355   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/md1: 497.9 GB, 497908973568 bytes
2 heads, 4 sectors/track, 121559808 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x08040000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 197 MB, 197263360 bytes
2 heads, 4 sectors/track, 48160 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md2: 1998 MB, 1998651392 bytes
2 heads, 4 sectors/track, 487952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x89983a19

Disk /dev/md2 doesn't contain a valid partition table

```

---

