---
title: "USB HD, Can't set config #1, error -110.  Can't enable legacy USB"
date: 2015-07-05
forum: Hardware
---

### Post by tbaac on 2015-07-05
Hi

I have an external Seagate hard disk with media on it.
This device is powered by an external power supply.

I upgraded from Ubuntu 12.4 LTS to 14.4 LTS and the USB disk has stopped being mountable when plugged in.
I did a fresh install of 12.4.5, did and apt-get update and then tried plugging it in, I still get the same problem.

From dmesg:

[ 1119.343426] usb 1-2: USB disconnect, device number 2
[ 1125.616081] usb 1-2: new high-speed USB device number 6 using ehci-pci
[ 1125.761257] usb 1-2: New USB device found, idVendor=0bc2, idProduct=3000
[ 1125.761266] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1125.761273] usb 1-2: Product: FreeAgentDesktop
[ 1125.761279] usb 1-2: Manufacturer: Seagate

[ 1130.760414] usb 1-2: can't set config #1, error -110

Googling or searching here for the error gives a number of results.
I have an old laptop (Asus A6M) and the bios does not have a Legacy USB option.

Is there another way to get my usb hard drive to mount?

Thanks very much.

---

