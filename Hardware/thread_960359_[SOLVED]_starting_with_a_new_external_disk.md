---
title: "[SOLVED] starting with a new external disk"
date: 2008-10-27
forum: Hardware
---

### Post by AceDip on 2008-10-27
I have just purchased a new external hard disk and want to use it for taking backup of my comp HDD.
But when i connect it to the usb,the comp doesn't show it though its connected..
kindly help me use it..

---

### Post by vanadium on 2008-10-27
My guess is that the ntfs file system of your external drive is not clean. If you only use Ubuntu, then I recommend reformatting the drive to the ext3 file system: do not use the ntfs file system. If you do have Windows, check and repair the file system using MS Windows. After that, Ubuntu will mount it automatically.

---

### Post by AceDip on 2008-10-27
i do not have windows.i just have ubuntu.here is some output.
/sda => HDD
/sdb => External drive
```
:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3f5d3f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         123      987966   82  Linux swap/Solaris
/dev/sda2   *         124         135       96390   83  Linux
/dev/sda3             136         743     4883760   83  Linux
/dev/sda4             744       19457   150320205    5  Extended
/dev/sda5             744       14116   107418591   83  Linux
/dev/sda6           14117       15332     9767488+  83  Linux
/dev/sda7           15333       19457    33134031   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217       19457   146520832+   5  Extended
/dev/sdb5            1217       19457   146520801   83  Linux


```

---

### Post by AceDip on 2008-10-27
But i'd prefer the logical drive in the external disk to be 'ntfs' so that i can use it at my friends computers...large data transfers u know ..

---

