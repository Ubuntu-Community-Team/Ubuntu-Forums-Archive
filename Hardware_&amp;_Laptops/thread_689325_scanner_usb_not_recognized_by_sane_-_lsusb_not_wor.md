---
title: "scanner usb not recognized by sane - lsusb not working"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by e_defranco on 2008-02-06
Hi,

I use xubuntu 7.10 and i have 1 usb wireless nic, 1 usb printer and 1 usb scanner.

Until some day ago all working fine, sane recognized the scanner and lsusb display all device.

But now, without apparent reason, the scanner is not recognized by sane and lsusb don't prodiuce any output.

The other usb device (fortunately) working fine.

there are some people that can help me ?

Thank in advance,

emilio

---

### Post by e_defranco on 2008-02-07
in /etc/fstab was missing this:

none /proc/bus/usb usbfs auto,devmode=0666 0 0

sane not working if usbfs is not mounted.

after re writing fstab with this line all working fine again :)

emilio

---

