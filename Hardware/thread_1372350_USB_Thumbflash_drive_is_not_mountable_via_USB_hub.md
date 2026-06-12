---
title: "USB Thumb/flash drive is not mountable via USB hub"
date: 2010-01-04
forum: Hardware
---

### Post by storckm on 2010-01-04
I have a Sony USB thumb drive which automounts normally, but when I insert it into a USB hub it not only won't automount, but doesn't even seem to show up as a device.  The hub works fine for mounting a digital camera, and I think I used it on another computer to mount the same flash drive.

Stranger still, when I run lsusb with the usb drive in the hub, it seems to detect the drive every other time.


flash drive: 054c:0243 Sony Corp. MicroVault Flash Drive (4Gb)
05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Thinkpad R52 running Xubuntu 9.10

---

### Post by K.J. on 2010-01-04
Is this a passive hub or an active one (does it have a power supply)? The USB hub might not be providing enough power. A camera has its own power and doesn't require any from USB.

Try putting the USB hub in a different port. PCs and laptops often have at least two USB hubs, and the one its on might be a bit too drained.

---

### Post by storckm on 2010-01-05
Thanks, that sounds reasonable.  Unfortunately, neither port seems able to power the drive through the hub (which isn't powered, as you guessed).
Regards,
MHS

---

### Post by darkksyde on 2010-01-06
The USB hub might not be providing enough power to drive the flash drive

---

