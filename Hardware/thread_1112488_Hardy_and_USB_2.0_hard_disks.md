---
title: "Hardy and USB 2.0 hard disks"
date: 2009-03-31
forum: Hardware
---

### Post by dlns on 2009-03-31
Hello,

I have a 200 GB USB 2.0 hard disk drive that used to work with my Thinkpad T40 (Ubuntu Hardy). For a few days now, since the last software update, it does no longer connect when I plug it in. dmesg just reports
```
[ 3105.304618] usb 5-4: new high speed USB device using ehci_hcd and address 17
```
Other USB 2.0 drives work fine, it's just the hard disk. dmesg does not report about partitions, neither does lsusb list it.

Removing the ehci_hcd module makes it work again, but only with USB 1.1 enabled. Which means a speed of about 1 MB/s. Which again means not much fun on a 200 GB FAT32 harddisk...

I figured out that there's a bug with the USB 2.0 device driver that's probably not to be fixed in near future. But as other USB 2.0 devices work with full speed on that machine and the hard disk also works with full speed on Intrepid, I don't think it is that bug...

Any hints or ideas are welcome. :)

Greetings, D.

---

