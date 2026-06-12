---
title: "Install a USB printer in Maverick 32-bit"
date: 2010-12-14
forum: Hardware
---

### Post by nicknefarious on 2010-12-14
I am trying to install a USB Receipt Printer in Ubuntu Maverick.

When I go into CUPS the USB option does not appear. I have tried restarting CUPS but this also seems to cause an error and returns a message.

If I ```
lsusb
``` the USB printer does not appear when attached. It works fine in XP and installs automatically.

Below is the syslog output when I connect the USB printer. Please can someone take a look at this and tell me what the problem is... I can see there is a problem. Exactly what? and how do I fix it?

Cheers for any help

Quote:
Dec 13 17:30:12 mavericks-main udev-configure-printer: remove /devices/pci0000:00/0000:00:12.1/usb4/4-1
Dec 13 17:30:12 mavericks-main kernel: [19977.800744] usb 4-1: USB disconnect, address 4
Dec 13 17:30:15 mavericks-main kernel: [19980.900525] usb 4-1: new full speed USB device using ohci_hcd and address 5
Dec 13 17:30:15 mavericks-main kernel: [19981.067140] usb 4-1: config 1 has an invalid interface number: 1 but max is 0
Dec 13 17:30:15 mavericks-main kernel: [19981.067144] usb 4-1: config 1 has 2 interfaces, different from the descriptor's value: 1
Dec 13 17:30:15 mavericks-main kernel: [19981.067149] usb 4-1: config 1 interface 0 altsetting 0 has 1 endpoint descriptor, different from the interface descriptor's value: 2
Dec 13 17:30:15 mavericks-main udev-configure-printer: add /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0
Dec 13 17:30:15 mavericks-main udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:12.1/usb4/4-1
Dec 13 17:30:15 mavericks-main udev-configure-printer: Device vendor/product is 0483:5740
Dec 13 17:30:16 mavericks-main udev-configure-printer: Failed to fetch Device ID
Dec 13 17:30:16 mavericks-main udev-configure-printer: invalid or missing IEEE 1284 Device ID

Thanks,

NN

---

