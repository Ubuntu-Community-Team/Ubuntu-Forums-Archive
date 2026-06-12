---
title: "USB Flash drive not working"
date: 2012-04-25
forum: Hardware
---

### Post by rob92 on 2012-04-25
Just got a new 32gb flash drive, but can't get it to work in ubuntu. It works in windows, and other usb devices and flash drives work on my laptop, so i'm guessing the hardware is fine. 

I'm running ubuntu 12.04 with gnome 3 shell.

I somehow managed to mount it manually but could not read or write.

Syslog repeatedly shows:

... kernel: [ 3510.160118] usb 1-8: reset high-speed USB device number 6 using ehci_hcd
... udevd[1974]: timeout: killing '/sbin/blkid -o udev -p /dev/sdb' [3663]

The devices does not show with fdisk, but lsusb shows:
Bus 001 Device 006: ID 0011:7788

Hope someone can help!

Thanks in advance

---

### Post by rob92 on 2012-04-27
Does no one have any ideas?

I've done countless searches to find a solution but so far nothing  has worked.

If it's any help i used windows to put a live version of lubuntu on the drive, it manages to get to the blue screen with lubuntu and the dots (loading screen) but gets stuck there.

---

### Post by rob92 on 2012-04-28
bump

---

