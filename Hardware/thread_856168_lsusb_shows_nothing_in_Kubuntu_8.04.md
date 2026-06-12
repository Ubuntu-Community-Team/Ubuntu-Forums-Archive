---
title: "lsusb shows nothing in Kubuntu 8.04"
date: 2008-07-11
forum: Hardware
---

### Post by wl2776 on 2008-07-11
usb flash drives and iPod work correctly, but lsusb doesn't output anything.

$ lsusb
$

$ ll /proc/bus/usb/
total 0
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 001
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 002
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 003
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 004
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 005
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 006
dr-xr-xr-x 2 root root 0 2008-07-11 10:55 007
-r--r--r-- 1 root root 0 2008-07-11 15:24 devices

$ lsmod | grep usb
usb_storage            73664  0
libusual               19108  1 usb_storage
scsi_mod              151436  5 sg,sr_mod,sd_mod,usb_storage,libata
usbcore               146028  5 usb_storage,libusual,ehci_hcd,uhci_hcd

What's wrong?
That command worked in previous version.

---

