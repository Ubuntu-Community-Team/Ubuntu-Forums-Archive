---
title: "USBFS mounts don't mount since upgrade to 2.6.31-18-generic on 64-bit Karmic"
date: 2010-01-17
forum: Hardware
---

### Post by eggplant37 on 2010-01-17
Updated kernel to 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:54:52 UTC 2010 x86_64 GNU/Linux yesterday from 2.6.31-17-generic. 

As a result, mounting usbfs via these two lines in /etc/fstab fails on -18, works fine in -17:

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

#mount -a
mount: mount point /proc/bus/usb does not exist
mount: mount point /proc/bus/usb does not exist

What changed to make this fubar?

---

### Post by GameManK on 2010-03-08
Looks like it's not supposed to work:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507824)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488274)

---

### Post by edonia on 2010-03-09
Same here.
I have a piece of very nice hardware, a sheet scanner, with linux software. It is not supported by the manufacture any more and does need to connect via /proc/bus/usb.
I did buy 2 of these scanners, because it was a long time the only one, to get for linux, is called "TravelScan PRO 2300U" or "pentax DSmobile".
This hardware is in daily use, but now stops working. I can not even find a solution to get it work again.
I'm disappointed :-(

---

### Post by mpr32 on 2010-03-09
I am glad I am not the only one having the problem. I have looked for any kind of work around. There have been forums stating to edit your mountdevsubfs.sh. and then edit fstab. Do not waste your time. If you have an updated machine you will not have this file (Located in /etc/init.d). If you find the file somewhere else don't bother to download it. The file will point to other directories and functions that are non-existent on your machine. If anyone can find an answer that would be nice.

---

### Post by edonia on 2010-03-09
so far, the only answer is to build your own kernel and enable the config option "USB_DEVICEFS", because the kernel is now compiled without "USB_DEVICEFS" :-(

---

### Post by edonia on 2010-03-09
hey stop!

I found a solution for my scanner (thanks to Alan):

```
mount --bind /dev/bus /proc/bus
```

although this will cause the other directories under /proc/bus to be 
hidden.

after running this command as root, the scanner is accessible again :-)

---

