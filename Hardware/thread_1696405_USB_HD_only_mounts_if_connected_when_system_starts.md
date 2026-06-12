---
title: "USB HD only mounts if connected when system starts, only seen with lsusb elsewise"
date: 2011-02-27
forum: Hardware
---

### Post by Ekeout on 2011-02-27
Hello.

Xubuntu 10.04
WD Passport 120GB USB hd does not automount when connected anymore.
 It mounts if it is plugged in while the system is starting up. fdisk is blind to it, lsusb is not. I know there's a thread regarding this and a solution I seem to recall involved modprobe, but after 30 mins of searching I haven't found it. So:

When plugged in after system has started, so spoketh:

lsusb:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:0702 Western Digital Technologies, Inc. Passport External HDD
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31a431a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4627    37162747+   7  HPFS/NTFS
/dev/sda2            4627       14594    80057345    5  Extended
/dev/sda5            4627        6451    14648437+  83  Linux
/dev/sda6           14182       14594     3304448   82  Linux swap / Solaris


What to do?

---

