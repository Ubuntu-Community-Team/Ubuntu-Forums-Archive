---
title: "hard disk data missing, need to retrive..help"
date: 2008-07-29
forum: Hardware
---

### Post by jovianic on 2008-07-29
Previously I dual boot xp and ubuntu with two different hard disk.
last week, the xp side (hdb) crashed,so I deleted, the c:\ only, with gparted, at first i can still access the d:\ part where all those mp3s, installer, movies etc under ubuntu OS.

Then i dec[PHP][/PHP]ided to increase my ubuntu (hda) ext3 size with gparted to accommodate the xp in qemu (boot XP in ubuntu).
then i mistakenly did something wrong during the process and have to reformat the ubuntu, edit fstab and the grub boot file thing.

Now, my ubuntu is working fine in this first hard disk, but days later when i reattached the second HD, the hdb5 (d:\ in XP) was not there.
I were very sure i only deleted the c:\ (hdb7) using gparted only.

When i use gparted to view the second HD details, it shows 7GB of "unallocated" disk space only. My total second HD space is 80GB, so where's is my other 73GB?
I believe the data is still somewhere, i try blindly to edit the fstab, search the forum about uuid, mounting etc, but it still won't work.

please help, I started using ubuntu 6 months ago only..thank you.

```

sudo fdisk -l


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1        4865    39078081    f  W95 Ext'd (LBA)
/dev/hda5              90        1619    12289725    b  W95 FAT32
/dev/hda6               1          89      714798   82  Linux swap / Solaris
/dev/hda7            1620        4865    26073463+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 8455 MB, 8455200768 bytes
16 heads, 63 sectors/track, 16383 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xfc48fd79

Disk /dev/hdb doesn't contain a valid partition table

```

it says "doesn't contain a valid partition table"...i only deleted the c:\ part, which left the d:\ (vfat)

---

### Post by warp99 on 2008-07-29
Only the partition information is missing, the data should still be there. Just use fdisk to restore the partition table and all should be well.

---

