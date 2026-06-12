---
title: "Microsoft Optical Desktop (wireless keyboard and mouse)"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by elahrairah on 2007-07-13
There are a lot of posts on this forum with similar issues, but I still haven't been able to get my Microsoft Wireless Optical Desktop keyboard or mouse to work. I am getting no input whatsoever from either the mouse or keyboard. I am running Feisty on a Dell Laptop d610. 

This set has a single base-station which connects by USB for both the keyboard and mouse. When I plug the basestation into the USB it seems to connect and reconnect again and again:

$ dmesg | tail -20
[260374.848000] usb 4-1: new low speed USB device using uhci_hcd and address 73
[260375.032000] usb 4-1: configuration #1 chosen from 1 choice
[260375.048000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43587
[260375.048000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260375.196000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43588
[260375.196000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260375.196000] usb 4-1: USB disconnect, address 73
[260376.108000] usb 4-1: new low speed USB device using uhci_hcd and address 74
[260376.292000] usb 4-1: configuration #1 chosen from 1 choice
[260376.308000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43589
[260376.308000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260376.460000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43590
[260376.460000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260376.460000] usb 4-1: USB disconnect, address 74
[260377.164000] usb 4-1: new low speed USB device using uhci_hcd and address 75
[260377.348000] usb 4-1: configuration #1 chosen from 1 choice
[260377.364000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43591
[260377.364000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260377.516000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43592
[260377.516000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1


It seems from this that it is just disconnecting and reconnecting over and over again. Neither the keyboard or mouse works at all (though I have tested the system on my windows laptop and both work fine).

Anyone have any ideas what this means, and how I could fix it?

Thanks for the help,
Megan

---

### Post by stchman on 2007-07-13
> **elahrairah said:**
> There are a lot of posts on this forum with similar issues, but I still haven't been able to get my Microsoft Wireless Optical Desktop keyboard or mouse to work. I am getting no input whatsoever from either the mouse or keyboard. I am running Feisty on a Dell Laptop d610. 

This set has a single base-station which connects by USB for both the keyboard and mouse. When I plug the basestation into the USB it seems to connect and reconnect again and again:

$ dmesg | tail -20
[260374.848000] usb 4-1: new low speed USB device using uhci_hcd and address 73
[260375.032000] usb 4-1: configuration #1 chosen from 1 choice
[260375.048000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43587
[260375.048000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260375.196000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43588
[260375.196000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260375.196000] usb 4-1: USB disconnect, address 73
[260376.108000] usb 4-1: new low speed USB device using uhci_hcd and address 74
[260376.292000] usb 4-1: configuration #1 chosen from 1 choice
[260376.308000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43589
[260376.308000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260376.460000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43590
[260376.460000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260376.460000] usb 4-1: USB disconnect, address 74
[260377.164000] usb 4-1: new low speed USB device using uhci_hcd and address 75
[260377.348000] usb 4-1: configuration #1 chosen from 1 choice
[260377.364000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43591
[260377.364000] input: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1
[260377.516000] input: Microsft Microsoft Wireless Optical Desktop&#65533; 2.10 as /class/input/input43592
[260377.516000] input: USB HID v1.11 Mouse [Microsft Microsoft Wireless Optical Desktop&#65533; 2.10] on usb-0000:00:1d.3-1


It seems from this that it is just disconnecting and reconnecting over and over again. Neither the keyboard or mouse works at all (though I have tested the system on my windows laptop and both work fine).

Anyone have any ideas what this means, and how I could fix it?

Thanks for the help,
Megan

It would not surprise me that M$ would have anti Linux EEPROMSs in their wireless products.  ;-)

JK, I have a Logitech wireless KB and Mouse that works flawlessly under Feisty.

When you connect the wireless KB and mouse can you get into the BIOS before the OS boots up?  Do you have USB KB selected as enabled in BIOS?

---

### Post by elahrairah on 2007-07-13
Well, I checked my BIOS but wasn't sure where to look, everything seemed enabled. I am succesfully able to use a USB keyboard and a USB mouse, but not this one.

---

