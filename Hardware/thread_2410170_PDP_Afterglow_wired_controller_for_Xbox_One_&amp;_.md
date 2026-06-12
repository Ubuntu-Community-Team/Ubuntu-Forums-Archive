---
title: "PDP Afterglow wired controller for Xbox One &amp; Windows"
date: 2019-01-11
forum: Hardware
---

### Post by doc taz on 2019-01-11
Just bought this recently. Several PDP controllers are supported on xpad. Tried xpad and xboxdrv.  Neither one seems to work, and jstest-gtk lists the wireless pads. 

Anyone out there successfully running this in Ubuntu/Linux?

from dmesg:
 
[  112.609259] usb 1-1: new full-speed USB device number 8 using xhci_hcd
[  112.737173] usb 1-1: New USB device found, idVendor=0e6f, idProduct=02b8, bcdDevice= 2.13
[  112.737174] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  112.737175] usb 1-1: Product: Afterglow Wired Controller for Xbox One
[  112.737176] usb 1-1: Manufacturer: Performance Designed Products

[ATTACH=CONFIG]282180[/ATTACH]

---

### Post by mikasu on 2019-01-12
I use this controller and it works no problem on Ubuntu 18.04.1. But you seem to have a different revision from mine. I have the older one with RGB tubes instead of LEDs.

---

### Post by doc taz on 2019-01-15
Upgraded to 18.10, which has the 4.19 kernels. 

dmesg output:

[   19.623203] usb 1-1: new full-speed USB device number 7 using xhci_hcd
[   19.751224] usb 1-1: New USB device found, idVendor=0e6f, idProduct=02b8, bcdDevice= 2.13
[   19.751225] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   19.751226] usb 1-1: Product: Afterglow Wired Controller for Xbox One
[   19.751227] usb 1-1: Manufacturer: Performance Designed Products
[   19.751228] usb 1-1: SerialNumber: 0000E62A9A63B220
[   19.759107] input: Generic X-Box pad as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input22
[   19.759198] usbcore: registered new interface driver xpad

jstest-gtk still doesn't work for calibration. It registers the game pad, but that's all I can do with it. No games can register the pad, either. 

Is there some config file I need to edit to make this pad work?

It obviously works in Win10, but... I could return this to the store and exchange it for a PDP pad that doesn't use any LED's... or a MS Xbox One pad.

---

### Post by mikasu on 2019-01-15
It's been a little while since they updated xpad, with Mircosoft's participation as I heard, and they added support for many custom firmware controllers like PDP's but you seem to have a more recent revision of the Prismatic Afterglow than I do. As I said, I have the old one that you can find easily on Google with the tubes for RGB lighting. It's not like yours with 3 LEDs. Perhaps they made another custom firmware on that revision that doesn't work with xpad at the moment. The problem is surely not the LEDs, it's the custom firmware, if you get a recent revision of a controller, it has less chances to work with the actual xpad, you might want to see if there are recent dev builds or wait for a new update of xpad.

---

### Post by doc taz on 2019-01-18
Ah, figured it out. Looked up the xpad.c file for the latest xpad drivers, and my controller is listed. For some reason (could be something with my laptop...?), it works best if the gamepad is attached before Linux boots. In any case, jstest can detect and calibrate the pad. Time to fire up a few Steam games to see if it works there, especially with the Windows titles under Proton. It does work with native games.

---

### Post by doc taz on 2019-01-18
{dp; deleted}

---

### Post by mikasu on 2019-01-18
Your controller is "listed" but it might be the older revision because they are both named the same. Unless they list both revisions, good luck on your tests :P

---

