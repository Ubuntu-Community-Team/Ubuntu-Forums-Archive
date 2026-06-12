---
title: "Get Pocket-PC connection"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by scaltro on 2007-10-22
I've problem with last Gutsy and my Pocket PC M700 eten.... I rebuild my own 2.6.23 kernel, including this module:
[LIST]
[*]ipaq
[*]usbserial
[*]usb-net capable (I don't remember module's name)
[/LIST]
I've installet all the software for syncing like Synce 0.10, Multisync. But the problem is at the beginning... When I connect my PDA, I can't get USB association like /dev/ttyUSB0, with dmesg I get this:```
drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5
usbcore: registered new interface driver ipaq
hub 3-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
usb 3-1: USB disconnect, address 5
usb 3-1: new low speed USB device using uhci_hcd and address 6
usb 3-1: configuration #1 chosen from 1 choice
input: HID 062a:0000 as /class/input/input11
input: USB HID v1.10 Mouse [HID 062a:0000] on usb-0000:00:1d.1-1
usb 2-1: new full speed USB device using uhci_hcd and address 2
usb 2-1: no configuration chosen from 1 choice
usb 2-1: USB disconnect, address 2
usb 2-1: new full speed USB device using uhci_hcd and address 3
usb 2-1: no configuration chosen from 1 choice
```

---

### Post by scaltro on 2007-10-23
Anyone know if I miss some kernel module?

---

### Post by aeg1s on 2007-11-03
I can confirm this problem with my own Pocket PC (hx2495) and Gutsy.  When I plug the hx2495 in via USB, nm-applet shows my wireless connection being dropped and it searches for a new connection (swirling animated icon)...  Eventually the icon changes to a computer and shows a 1MB LAN connection.  I haven't been able to get anywhere after that.

---

