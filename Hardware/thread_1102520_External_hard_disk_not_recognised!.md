---
title: "External hard disk not recognised!"
date: 2009-03-21
forum: Hardware
---

### Post by Yvan300 on 2009-03-21
Hello I have a 36gb netdisk ndas mini formatted in ntfs and for some reason it is not recognized by ubuntu. The activity led is constantly on and maybe this info could help.

lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 12c8:1f05  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and

fdisk
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2            6000        6947     7614810   83  Linux
/dev/sda3   *          12        5999    48098610   83  Linux
/dev/sda4            6948        7296     2803342+   5  Extended
/dev/sda5            6948        7296     2803311   82  Linux swap / Solaris

Partition table entries are not in disk order

This information was taken while the drive was plugged in.
Please help!

---

### Post by kevinbeard on 2009-05-13
NDAS devices are not currently supported on 9.04 I'm afraid.

They work fine with 8.10 but until someone fixes the driver they remain broken 

See:

[http://ubuntuforums.org/showthread.p...ht=ndas&page=2](http://ubuntuforums.org/showthread.p...ht=ndas&page=2)

and

[http://ubuntuforums.org/showthread.p...ht=ndas&page=3](http://ubuntuforums.org/showthread.p...ht=ndas&page=3)

---

### Post by Yvan300 on 2009-05-13
Oh sorry fo that, i actually made this thread when i was using ibex, but in jaunty my external drive works great, thanks for your help :)

---

