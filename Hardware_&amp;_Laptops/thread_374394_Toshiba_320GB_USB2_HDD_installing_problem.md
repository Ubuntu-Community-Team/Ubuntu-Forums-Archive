---
title: "Toshiba 320GB USB2 HDD installing problem"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by reza81 on 2007-03-02
I just got a new external hdd (Toshiba 320GB USB2 HDD) so I can copy data from my another NTFS USB 2 HDD on this one and format it to ext3.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         272     2184808+  82  Linux swap / Solaris
/dev/hda2             273        2567    18434587+  83  Linux
/dev/hda3            2568        9729    57528765   83  Linux

Disk /dev/sdf: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       14946   120053713+   7  HPFS/NTFS
```

```
reza@reza-desktop:~$ lsusb
[B]Bus 005 Device 009: ID 0930:0b05 Toshiba Corp. 
Bus 005 Device 007: ID 20c8:3574  
Bus 005 Device 001: ID 0000:0000  [/B]
Bus 001 Device 004: ID 046d:c00e Logitech, Inc. M-BJ69 Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 1025:0041 Hyper-Paltek 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:0200 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 147a:e00d Formosa Industrial Computing, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

this is what i see... it allso has some kind of lame password protection on it.

how can I formate this ???

P.S. Gnome Partition manager doesn't see the new USB HDD
Edit/Delete Message

---

### Post by reza81 on 2007-03-04
Isn't there anyone wo can help me with this ???

---

