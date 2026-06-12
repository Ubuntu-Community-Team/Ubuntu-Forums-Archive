---
title: "Iomega Ego Won't Mount :|"
date: 2011-03-10
forum: Hardware
---

### Post by Dante311 on 2011-03-10
I just bought an Ego Iomega 500 gb external HD today and to my dismay it won't mount.  I plug it into my machine and nothing happens.  I am using Ubuntu 9.10 but I bought the HD to back up my information and update to 10.04.

Any advice?

---

### Post by Dante311 on 2011-03-10
I thought I would add this information as I have seen in other threads involving HDs.

sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13803   110871573+   7  HPFS/NTFS
/dev/sda2           18693       19458     6140928   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           13804       18692    39270892+   5  Extended
/dev/sda5           18368       18670     2433816   83  Linux
/dev/sda6           18671       18692      176683+  82  Linux swap / Solaris
/dev/sda7           13804       18174    35109994+  83  Linux
/dev/sda8           18175       18367     1550241   82  Linux swap / Solaris

Partition table entries are not in disk order


lsusb

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:080a Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d09 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The hard drive doesn't appear in these lists.

---

### Post by runeh76 on 2011-03-10
Hi

U have 2 usb2 ports..try another port and remove all other usb devices.

---

### Post by Dante311 on 2011-03-10
I tried removing other devices and plugging into the other 2 slots but still doesn't show up.  It also doesn't display anything in the lsusb command.

---

### Post by runeh76 on 2011-03-10
U get more information with: ```
lsusb -v
```

Maybe its broken?

---

### Post by Dante311 on 2011-03-10
I fiddled with cords unplugging and plugging and now I got a connection.  Thanks for the input.  Glad it was easy fix!

---

