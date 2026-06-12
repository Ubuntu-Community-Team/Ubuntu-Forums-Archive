---
title: "usb 5-button mouse (MouseTrapper)"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by spaceman_spiff on 2006-08-09
I'm having trouble getting my MouseTrapper 5-button usb mouse detected in dapper. From lsusb I get USB ID 0d24:0004. 

This mouse worked fine in breezy. Is there an easy way to have ubuntu recognize this USB ID as another 5-button usb mouse? Perhaps this was what happened in breezy?

dmesg shows this kind of connect-disconnect action when I connect the mouse:

---
[17279202.592000] usb 3-2: new low speed USB device using uhci_hcd and address 32
[17279202.784000] input: Trapper Data AB MouseTrapper&#65533; Electronic as /class/input/input32
[17279202.784000] input: USB HID v1.10 Mouse [Trapper Data AB MouseTrapper&#65533; Electronic] on usb-0000:00:1d.2-2
[17279203.864000] usb 3-2: USB disconnect, address 32
[17279204.608000] usb 3-2: new low speed USB device using uhci_hcd and address 33
[17279204.800000] input: Trapper Data AB MouseTrapper&#65533; Electronic as /class/input/input33
[17279204.800000] input: USB HID v1.10 Mouse [Trapper Data AB MouseTrapper&#65533; Electronic] on usb-0000:00:1d.2-2
[17279205.880000] usb 3-2: USB disconnect, address 33
[17279206.624000] usb 3-2: new low speed USB device using uhci_hcd and address 34
[17279206.816000] input: Trapper Data AB MouseTrapper&#65533; Electronic as /class/input/input34
[17279206.816000] input: USB HID v1.10 Mouse [Trapper Data AB MouseTrapper&#65533; Electronic] on usb-0000:00:1d.2-2
[17279207.896000] usb 3-2: USB disconnect, address 34
[17279208.640000] usb 3-2: new low speed USB device using uhci_hcd and address 35
[17279208.888000] input: Trapper Data AB MouseTrapper&#65533; Electronic as /class/input/input35
[17279208.888000] input: USB HID v1.10 Mouse [Trapper Data AB MouseTrapper&#65533; Electronic] on usb-0000:00:1d.2-2
[17279209.912000] usb 3-2: USB disconnect, address 35
[17279210.656000] usb 3-2: new low speed USB device using uhci_hcd and address 36
[17279210.848000] input: Trapper Data AB MouseTrapper&#65533; Electronic as /class/input/input36
[17279210.848000] input: USB HID v1.10 Mouse [Trapper Data AB MouseTrapper&#65533; Electronic] on usb-0000:00:1d.2-2
[17279211.928000] usb 3-2: USB disconnect, address 36
---

---

