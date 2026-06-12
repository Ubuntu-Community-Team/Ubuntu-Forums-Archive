---
title: "USB Scanner Connection Issue"
date: 2020-03-12
forum: Hardware
---

### Post by bilkay on 2020-03-12
I have a Brother ADS-1200 scanner that works fine until I turn it off while connected via USB.

When I first plug it in or startup with it connected, xsane finds it and lsusb shows the usb device. Usually, When I unplug the usb cable, lsusb shows it gone, and then usually if I plug it back in, it shows up in lsusb and xsane finds it. However, if I turn the scanner power off while it's plugged in, lsusb shows it gone, but I can not then get the device to show up on lsusb without doing a reboot.

I have another scanner with a scsi interface, and have a similar problem which is rectified by removing and reinserting a kernel module. I don't see a similar fix for this.

---

