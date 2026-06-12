---
title: "can someone help me formatting my usb stick"
date: 2012-07-03
forum: Hardware
---

### Post by blackoutfh on 2012-07-03
blackout@roman:~$ sudo fdisk -l
[sudo] password for blackout: 

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000390c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117229567    58613760   83  Linux

Disk /dev/mmcblk0: 7964 MB, 7964983296 bytes
4 heads, 16 sectors/track, 243072 cylinders, total 15556608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a9b03

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              16    15556607     7778296   83  Linux



Bus 002 Device 016: ID 13fe:5000 Kingston Technology Company Inc. 

with sudo dd if=/dev/zero of=/dev/sdb1
it writes me only 3gb of 16gb

with this 3gb

                           cfdisk (util-linux 2.20.1)

                             Disk Drive: /dev/sdb1
                        Size: 3111960576 bytes, 3111 MB
              Heads: 87   Sectors per Track: 60   Cylinders: 1164

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sdb1p1      Boot, NC    Primary   Linux                             3111.97*



dmesg
[ 8106.348120] usb 2-1.2: USB disconnect, device number 16
[ 8108.594237] usb 2-1.2: new high-speed USB device number 17 using ehci_hcd
[ 8109.077058] scsi16 : usb-storage 2-1.2:1.0


blackout@roman:~$ sudo mount /dev/sdb1 /media/sh
mount: you must specify the filesystem type


but there is no way to format the disk or use it in any way

some ideas??

with windows it can not be low level formatted because it's recognized as not connected

---

