---
title: "[Ubuntu 18.04] Keystation Mini 32 midi keyboard not working"
date: 2019-06-21
forum: Hardware
---

### Post by joard on 2019-06-21
Hi,

I'm having trouble getting Ubuntu to recognise my usb midi keyboard (Keystation Mini 32). It does not show up in lsusb, and dmesg gives the following output after plugging in the keyboard:

```

[  393.639598] usb 2-1: new full-speed USB device number 12 using xhci_hcd
[  393.767782] usb 2-1: device descriptor read/64, error -71
[  394.003627] usb 2-1: device descriptor read/64, error -71
[  394.239573] usb 2-1: new full-speed USB device number 13 using xhci_hcd
[  394.367739] usb 2-1: device descriptor read/64, error -71
[  394.603786] usb 2-1: device descriptor read/64, error -71
[  394.711770] usb usb2-port1: attempt power cycle
[  395.367746] usb 2-1: new full-speed USB device number 14 using xhci_hcd
[  395.367920] usb 2-1: Device not responding to setup address.
[  395.575958] usb 2-1: Device not responding to setup address.
[  395.783768] usb 2-1: device not accepting address 14, error -71
[  395.911772] usb 2-1: new full-speed USB device number 15 using xhci_hcd
[  395.911894] usb 2-1: Device not responding to setup address.
[  396.119700] usb 2-1: Device not responding to setup address.
[  396.327631] usb 2-1: device not accepting address 15, error -71
[  396.327730] usb usb2-port1: unable to enumerate USB device

```

The keyboard does work on a windows 10 laptop, on both usb2.0 and 3.0 ports, using the same cable so I know that it isn't a problem with the cable or keyboard itself. 

Thanks in advance

---

### Post by Autodave on 2019-06-22
Until someone way more knowledgeable than me comes along, try turning the keyboard on and connect to PC.  Then, power up the PC.

---

### Post by joard on 2019-06-24
Thanks for your reply.

> try turning the keyboard on and connect to PC.  Then, power up the PC.

Didn't work, still not visible in lsusb and dmesg gives the same output.

---

