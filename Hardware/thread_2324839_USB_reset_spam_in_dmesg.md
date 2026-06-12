---
title: "USB reset spam in dmesg"
date: 2016-05-16
forum: Hardware
---

### Post by xen3 on 2016-05-16
Pardon for this weird post.

I have and had a USB device (stick) that outputted lots of lines:

kernel: [------.------] usb 2-3: reset high-speed USB device number 2 using ehci-pci

I was able to turn that output off using:

sudo echo 1 > /sys/devices/pci0000:00/0000:00:13.2/usb2/2-3/avoid_reset_quirk

---

