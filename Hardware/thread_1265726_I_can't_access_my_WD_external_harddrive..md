---
title: "I can't access my WD external harddrive."
date: 2009-09-13
forum: Hardware
---

### Post by Bensky5012 on 2009-09-13
It has showed up in the past, and I can see it on my windows machine, but for some reason its not popping up on the desktop like it was before and its not in Places.

This is the output of sudo fdisk -l:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

Device Boot Start End Blocks Id System
/dev/sdb1 1 38913 312568641 c W95 FAT32 (LBA)

The 320 gb is the external.

Here is the output to lsusb:

Bus 001 Device 003: ID 1058:0705 Western Digital Technologies, Inc.
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046e:5542 Behavior Tech. Computer Corp.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

My external is the top entry (The western digital entry)

---

