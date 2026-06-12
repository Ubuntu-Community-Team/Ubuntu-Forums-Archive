---
title: "Can't Add Printer LX-300 on 10.04"
date: 2010-10-01
forum: Hardware
---

### Post by widoyo on 2010-10-01
I want to add my old printer on ubuntu 10.04 with Aten USB-to-parallel.

The Aten itself detected.

widoyo@3810T:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0557:2006 ATEN International Co., Ltd UC-1284B Printer Port <<< USB-to-parallel
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15ca:00c3 Textech Internatio <DELETED>

lp0 also detected.

widoyo@3810T:~$ ls /dev/usb/lp0
/dev/usb/lp0

Getting info about printerid the result is change when reconnect the USB

widoyo@3810T:~$ sudo usb_printerid /dev/usb/lp0
GET_DEVICE_ID string:
&#65533;&#65533;/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0ACTION=addDEVPATH=/devices/pc

widoyo@3810T:~$ sudo usb_printerid /dev/usb/lp0
GET_DEVICE_ID string:
2&#65533;&#65533;&#65533;
o/org/freedesktop/DBussorg.freedesktop.DBus

Using menu System > Administration > Printing | Add Printer can't find any local printer.

I type anything on field of "Enter device URI" but "forward" button still disabled. So I can not add printer.

Thank you for any help.

Widoyo

---

