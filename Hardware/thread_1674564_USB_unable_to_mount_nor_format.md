---
title: "USB unable to mount nor format"
date: 2011-01-24
forum: Hardware
---

### Post by dokyounder on 2011-01-24
When I plug this usb in, I can't find the usual usb icon that appears on the home screen. when I type sudo fdisk -l, it appears to be detected.
Following is the result from fdisk -l

```
Disk /dev/sdb: 4105 MB, 4105175040 bytes
127 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a168b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         960     3775488   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(470, 39, 17) logical=(959, 29, 60)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             960        1019      230401    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(470, 71, 48) logical=(959, 62, 61)
Partition 2 has different physical/logical endings:
     phys=(498, 246, 4) logical=(1018, 2, 16)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             960        1019      230400   82  Linux swap / Solaris

```

can anyone help me formatting this usb drive? I want every data on the usb gone. I just want to fix the problem so I can use it again.

---

### Post by ellgor on 2011-01-24
Hi,

You might want to format that drive in to a Linux friendly one ( underneath where it says /dev/sda1 : at the end of the line it says in brackets (non-linux), Gparted can do this quite quickly.

Regards, Ellgor.

---

### Post by dokyounder on 2011-01-25
I tried Gparted, but it doesn't work. It shows the partitions though. When I delete everything and click apply, it goes to the loading screen, but it takes forever without any progress, and eventually generates an error message. what's wrong with my usb??

---

