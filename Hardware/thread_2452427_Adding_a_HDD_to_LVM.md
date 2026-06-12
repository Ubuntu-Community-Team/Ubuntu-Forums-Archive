---
title: "Adding a HDD to LVM?"
date: 2020-10-21
forum: Hardware
---

### Post by Raymond Day on 2020-10-21
For a long time have two USB drives both 128GB as one drive so 256GB. I was running out of space so have a 256GB SSD and want to add it to make the LVM bigger. But looks like I just added another LVM as 256GB I can't get them to be as one.

Some commands on the command line my help to know how I should do this.

```
root@rayday1:~# lvmdiskscan
  /dev/loop0        [     <62.09 MiB]
  /dev/sda          [     238.47 GiB]
  /dev/loop1        [     217.89 MiB]
  /dev/sda1         [     238.44 GiB] LVM physical volume
  /dev/mmcblk0p1    [     512.00 MiB]
  /dev/loop2        [      55.32 MiB]
  /dev/mmcblk0p2    [     <26.69 GiB]
  /dev/loop3        [      50.67 MiB]
  /dev/mmcblk0p3    [       1.93 GiB]
  /dev/loop4        [     <30.94 MiB]
  /dev/mmcblk0boot0 [       4.00 MiB]
  /dev/mmcblk0boot1 [       4.00 MiB]
  /dev/sdb1         [      <3.64 TiB]
  /dev/sdc1         [      <3.64 TiB]
  /dev/sdd1         [     116.37 GiB] LVM physical volume
  /dev/sde1         [     116.37 GiB] LVM physical volume
  1 disk
  12 partitions
  0 LVM physical volume whole disks
  3 LVM physical volumes
root@rayday1:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/256as1
  LV Name                256as1
  VG Name                vg1
  LV UUID                rx3N0S-xIBA-v0QV-Pb6z-nG1D-cr68-qnCbQb
  LV Write Access        read/write
  LV Creation host, time g8picuntu-MK802IV, 2014-05-30 17:34:13 -0400
  LV Status              available
  # open                 1
  LV Size                232.00 GiB
  Current LE             59392
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

  --- Logical volume ---
  LV Path                /dev/vg1/256GB_as_One
  LV Name                256GB_as_One
  VG Name                vg1
  LV UUID                hahhAx-RFw1-D1K4-F2co-PBwZ-yZcF-p1bw6W
  LV Write Access        read/write
  LV Creation host, time LINUXIUMONE, 2015-01-13 22:06:22 -0500
  LV Status              available
  # open                 0
  LV Size                239.15 GiB
  Current LE             61223
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1

root@rayday1:~# lvm lvextend -l +100%FREE /dev/vg1/256as1
  New size (59392 extents) matches existing size (59392 extents).
root@rayday1:~# lvmdiskscan -l
  WARNING: only considering LVM devices
  /dev/sda1         [     238.44 GiB] LVM physical volume
  /dev/sdd1         [     116.37 GiB] LVM physical volume
  /dev/sde1         [     116.37 GiB] LVM physical volume
  0 LVM physical volume whole disks
  3 LVM physical volumes
root@rayday1:~# pvscan
  PV /dev/sde1   VG vg1             lvm2 [116.37 GiB / 0    free]
  PV /dev/sdd1   VG vg1             lvm2 [116.37 GiB / 0    free]
  PV /dev/sda1   VG vg1             lvm2 [238.41 GiB / 0    free]
  Total: 3 [471.15 GiB] / in use: 3 [471.15 GiB] / in no VG: 0 [0   ]
root@rayday1:~# pvs
  PV         VG  Fmt  Attr PSize   PFree
  /dev/sda1  vg1 lvm2 a--  238.41g    0
  /dev/sdd1  vg1 lvm2 a--  116.37g    0
  /dev/sde1  vg1 lvm2 a--  116.37g    0
root@rayday1:~# pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sde1
  VG Name               vg1
  PV Size               116.37 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              29791
  Free PE               0
  Allocated PE          29791
  PV UUID               drEiZE-oA0G-Pjhy-s9Q2-Sxsx-kyfN-6wB3VS

  --- Physical Segments ---
  Physical extent 0 to 29790:
    Logical volume      /dev/vg1/256as1
    Logical extents     0 to 29790

  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               vg1
  PV Size               116.37 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              29791
  Free PE               0
  Allocated PE          29791
  PV UUID               n7kScB-m7FH-bhvX-r4Hk-xBv2-FbtL-R5GzFv

  --- Physical Segments ---
  Physical extent 0 to 29600:
    Logical volume      /dev/vg1/256as1
    Logical extents     29791 to 59391
  Physical extent 29601 to 29790:
    Logical volume      /dev/vg1/256GB_as_One
    Logical extents     0 to 189

  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               vg1
  PV Size               238.44 GiB / not usable 29.66 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              61033
  Free PE               0
  Allocated PE          61033
  PV UUID               Wc8nDM-gFHc-jlC1-9uN2-y1ln-0GyD-Gnya9Q

  --- Physical Segments ---
  Physical extent 0 to 61032:
    Logical volume      /dev/vg1/256GB_as_One
    Logical extents     190 to 61222

root@rayday1:~#
```

Spent about all day on this and can't get it how I want it. I guess I could start all over if need to and then copy the files to it again when it's about 512GB insize.

-Raymond Day

---

### Post by Raymond Day on 2020-10-21
I think I got it now. Unmounted the 2 as 1 and then in Webmin could delete it and add all 3 as one. Format it and mount it. It worked. Coping files to it now. Should not run out of space now.

> Now it shows like this:

root@rayday1:~# pvdisplay -m
  --- Physical volume ---
  PV Name               /dev/sde1
  VG Name               vg1
  PV Size               116.37 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              29791
  Free PE               0
  Allocated PE          29791
  PV UUID               drEiZE-oA0G-Pjhy-s9Q2-Sxsx-kyfN-6wB3VS

  --- Physical Segments ---
  Physical extent 0 to 29790:
    Logical volume      /dev/vg1/512in3
    Logical extents     61033 to 90823

  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               vg1
  PV Size               116.37 GiB / not usable 3.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              29791
  Free PE               0
  Allocated PE          29791
  PV UUID               n7kScB-m7FH-bhvX-r4Hk-xBv2-FbtL-R5GzFv

  --- Physical Segments ---
  Physical extent 0 to 29790:
    Logical volume      /dev/vg1/512in3
    Logical extents     90824 to 120614

  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               vg1
  PV Size               238.44 GiB / not usable 29.66 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              61033
  Free PE               0
  Allocated PE          61033
  PV UUID               Wc8nDM-gFHc-jlC1-9uN2-y1ln-0GyD-Gnya9Q

  --- Physical Segments ---
  Physical extent 0 to 61032:
    Logical volume      /dev/vg1/512in3
    Logical extents     0 to 61032

root@rayday1:~#


-Raymond Day

---

### Post by TheFu on 2020-10-21
More compact output:
```
sudo pvs
sudo vgs
sudo lvs
```

Spanning LVs across multiple disks is asking to lose all the data on both, especially with a USB connection.  Hope doesn't happen to you like it did to me.  But if you have good backups, go for it!

---

