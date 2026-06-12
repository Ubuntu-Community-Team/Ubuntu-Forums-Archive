---
title: "USB Belkin HUB not working"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by Florent on 2005-07-03
Hi,

I have a Belkin 4 ports USB HUB that currently does not work with Ubuntu Hoary 2.6.10-5-k7.
Powerlight is on when plug it in, but then nothing happens when I plug a usb key or anything else in it. usb key is working fine if I plug it directly without the Hub.

Here is the content of dmesg just after I plug the Hub:
> 
usb 2-3: new full speed USB device using ohci_hcd and address 6
usb 2-3: device descriptor read/64, error -110
usb 2-3: device descriptor read/64, error -110
usb 2-3: new full speed USB device using ohci_hcd and address 7
usb 2-3: device descriptor read/64, error -110
usb 2-3: device descriptor read/64, error -110

And there is no hub detected with lsusb
> Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000

Any help is greatly apreciated.
Thanks

---

### Post by Florent on 2005-11-16
OK, forget it. After many tests, it appears that the hardware was out of order.
I finally bought a new one.

Sorry for disturbing. :(

---

