---
title: "Mounting external HDD with invalid partition table"
date: 2010-12-02
forum: Hardware
---

### Post by jindrichm on 2010-12-02
I'm trying to mount an external HDD connected via USB bridge. This is the USB bridge:

```
$ lsusb
Bus 002 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge

```

When I run sudo fdisk -l, it prints out:

```
Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

```

When I open GParted and examine the external HDD at /dev/sdc, it prints: 

```
/dev/sdc: unrecognised disk label

```

How should I proceed? Do I need to repair the partition table first?

---

