---
title: "insufficient available bus power"
date: 2020-08-06
forum: Hardware
---

### Post by majest2 on 2020-08-06
I have a new Dell desktop with a keyboard that has 2 usb slots.

When I first started using the computer, the 2 usb slots worked. I could read/write to a USB stick and also charge my cell phone. However about 1-2 months ago they stopped working.

The output on dmesg -w is:

> [19545.247877] usb 1-12.1: new high-speed USB device number 16 using xhci_hcd
[19545.352797] usb 1-12.1: New USB device found, idVendor=0781, idProduct=5575, bcdDevice= 1.00
[19545.352803] usb 1-12.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[19545.352807] usb 1-12.1: Product: Cruzer Glide
[19545.352810] usb 1-12.1: Manufacturer: SanDisk
[19545.352813] usb 1-12.1: SerialNumber: 4C530001301112212317312
[19545.353074] usb 1-12.1: **rejected 1 configuration due to insufficient available bus power**
[19545.353077] usb 1-12.1: no configuration chosen from 1 choice

It's very sad. The fact it used to work gives me hope that it might work again one day - google doesn't provide many clues for this problem. Can anyone advise what to do? Can I edit the "configuration" somehow?

---

### Post by CatKiller on 2020-08-06
Did you change which port the keyboard was plugged into 1-2 months ago?

---

### Post by majest2 on 2020-08-06
Maybe but I've tried it in every port since :)

---

