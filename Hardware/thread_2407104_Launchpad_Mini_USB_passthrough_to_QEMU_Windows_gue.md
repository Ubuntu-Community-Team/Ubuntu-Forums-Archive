---
title: "Launchpad Mini USB passthrough to QEMU Windows guest"
date: 2018-11-29
forum: Hardware
---

### Post by ytterbious on 2018-11-29
I have been trying to passthrough the Launchpad Mini connection to my QEMU Windows guest VM, but I can't seem to find the device in the Ubuntu host. Using the programs: ```
lsusb
``` ```
usb-devices
``` ```
lsinput
``` all show nothing. My process with each program has been to remove the USB cable, run the program to find the number of entries, and then plug the cable in again and run the program again to see if anything new appears. Each time, I find nothing. I have tried variants with and without a USB hub, as well as 4 different micro-USB cables, and nothing has changed, so I think the problem lies with Ubuntu and not my hardware (especially since this device was detected in Host Windows previously). I know there aren't any Linux drivers for this device, but I would still expect that the device would still be detected as being connected at some level.

Thanks all

---

