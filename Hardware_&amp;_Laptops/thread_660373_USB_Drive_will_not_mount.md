---
title: "USB Drive will not mount"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by 2tired on 2008-01-06
Well, I ran into another problem that I  can't figure out. I have a usb drive that had mounted fine until one day I had unplugged it and now it will not mount. The drive icon shows under the places/computer tab, but when I go to mount it, it comes up with and error and tells you to use the force option. I tired to just unplug my thumb drive and plug it back in without unmounting it and could not repeat the error. But all my hard drives ( usb that is ) will not mount. Anyone know how to fix this?:mad:

---

### Post by Alex135 on 2008-01-06
Whats the output of *sudo fdisk -l* when they are plugged in?

---

### Post by 2tired on 2008-01-07
Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d48b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       29834   239641573+  83  Linux
/dev/hdc2           29835       30401     4554427+   5  Extended
/dev/hdc5           29835       30401     4554396   82  Linux swap / Solaris

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496    7  HPFS/NTFS

Here is the output, when the drive is first installed it says it will not mount ntfs is in use????:shock::

---

