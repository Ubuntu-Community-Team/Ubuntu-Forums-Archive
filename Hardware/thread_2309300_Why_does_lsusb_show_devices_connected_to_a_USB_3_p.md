---
title: "Why does lsusb show devices connected to a USB 3 port as connected to USB2 root hub?"
date: 2016-01-09
forum: Hardware
---

### Post by marcosscriven on 2016-01-09
I'm running Ubuntu on a Dell Chromebook 11, which has two USB 3 ports, and an SD card reader. I was trying to establish whether the SD card reader would be capable of USB 3 speeds (and thus whether it's worth buying a 130MB/s SD card), but I can't tell whether it's physically connected to USB 3 internally.

One way I thought I might do this is to run lsusb after plugging in an SD card - however, if I plug in a USB2 device to one of the USB 3 ports, it comes up as being connected to the USB 2 hub anyway. If I put a USB 3 device into the very same port, it shows as a being connected to the USB 3 hub.

1) Why does lsusb show USB2 devices connected to a USB3 port as being attached to the USB 2 root?
2) Is there a way to get the physical rather than logical mapping of USB ports to hubs?
3) Coming back to my original reason for looking into this, is there a way to tell what speed the internal SD card reader is capable of before buying one?

---

