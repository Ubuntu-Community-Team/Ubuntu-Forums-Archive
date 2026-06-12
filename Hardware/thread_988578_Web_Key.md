---
title: "Web Key"
date: 2008-11-20
forum: Hardware
---

### Post by clearloon on 2008-11-20
I've got a web key and I'd like to have a look at what's on it but it isn't automatically mounted and I can't seem to mount it. I really don't know what do do to get started - any suggestions?

tail /var/log/messages outputs:

> Nov 20 21:57:42 home kernel: [12094.646342] usbcore: registered new interface driver hiddev              
Nov 20 21:57:42 home kernel: [12094.653782] input: WEB KEY WEB KEY as /devices/pci0000:00/0000:00:13.4/usb5/5-1/5-1:1.0/input/input6
Nov 20 21:57:42 home kernel: [12094.696757] input,hidraw0: USB HID v1.10 Keyboard [WEB KEY WEB KEY] on usb-0000:00:13.4-1
Nov 20 21:57:42 home kernel: [12094.696800] usbcore: registered new interface driver usbhid
Nov 20 21:57:42 home kernel: [12094.696806] usbhid: v2.6:USB HID core driver
Nov 20 22:04:40 home kernel: [12512.882240] usb 5-1: USB disconnect, address 2
Nov 20 22:04:42 home kernel: [12514.960529] usb 5-2: new low speed USB device using ohci_hcd and address 3
Nov 20 22:04:42 home kernel: [12515.130980] usb 5-2: configuration #1 chosen from 1 choice
Nov 20 22:04:42 home kernel: [12515.136999] input: WEB KEY WEB KEY as /devices/pci0000:00/0000:00:13.4/usb5/5-2/5-2:1.0/input/input7
Nov 20 22:04:42 home kernel: [12515.185037] input,hidraw0: USB HID v1.10 Keyboard [WEB KEY WEB KEY] on usb-0000:00:13.4-2

---

