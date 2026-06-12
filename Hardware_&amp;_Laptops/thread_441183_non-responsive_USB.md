---
title: "non-responsive USB"
date: 2007-05-12
forum: Hardware &amp; Laptops
---

### Post by Coops on 2007-05-12
Right, as of last night the USB system has fallen silent.

(amd64, feisty, foxxcon/winfast 6150k8ma mobo, 2.6.20-15, 2.6.20-14 & 2.6.17-10 [also Live CD]).

$ dmesg | grep usb
[   52.543893] usbcore: registered new interface driver usbfs
[   52.543957] usbcore: registered new interface driver hub
[   52.544012] usbcore: registered new device driver usb
[   52.617809] usb usb1: configuration #1 chosen from 1 choice
[   55.122886] usb usb2: configuration #1 chosen from 1 choice

(in rescue mode it prints that its found 8 usb ports).

However plugging and unplugging devices makes no activity in dmesg.

Plugging in a usb-hdd and manually modprobing usb-storage loads the module fine, but no sign of the device.

$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

$ lsmod | grep usb
usbcore               154416  3 ohci_hcd,ehci_hcd

I'm lost on this one!

Cheers.

Coops.

---

