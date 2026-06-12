---
title: "Gutsy xpad module sort of detects dance pad?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by cmatheson on 2007-10-26
Hi,

I hacked a couple XBOX dancepads to work w/ my PC.  It definitely works in Windows, but I'm not getting much luck in Linux (running Gutsy).  This is what happens when I plug it in:

Oct 26 19:12:04 winston kernel: [ 1891.875180] usb 5-2: new full speed USB device using uhci_hcd and address 14
Oct 26 19:12:04 winston kernel: [ 1892.028265] usb 5-2: configuration #1 chosen from 1 choice
Oct 26 19:12:04 winston kernel: [ 1892.031199] hub 5-2:1.0: USB hub found
Oct 26 19:12:04 winston kernel: [ 1892.034162] hub 5-2:1.0: 3 ports detected
Oct 26 19:12:05 winston kernel: [ 1892.348094] usb 5-2.1: new full speed USB device using uhci_hcd and address 15
Oct 26 19:12:05 winston kernel: [ 1892.469163] usb 5-2.1: configuration #1 chosen from 1 choice
Oct 26 19:12:05 winston kernel: [ 1892.513868] usbcore: registered new interface driver xpad
Oct 26 19:12:05 winston kernel: [ 1892.513875] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6

so it sort of does something w/ the xpad driver, but there aren't any /dev/input/js devices created.  Any clues as to what might be wrong?  I thought that everything after 2.6.19 kernel was supposed to be pretty good in terms of old xbox controllers/dance pads.

TIA,
Cam

---

