---
title: "USB Device Descriptor Error"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by bhogg on 2006-09-14
Hi all,

Just sat down at the computer today and the USB hub/switch is no longer recognized.  Tried multiple configurations of cables, resetting the device, etc. and will not work with the Ubuntu desktop.  Switching to the laptop and using the usb hub/switch works great.

I'm receiving the following messages in dmesg when I plug/unplug the device:

```
[4294794.225000] usb 3-4: new high speed USB device using ehci_hcd and address 7
[4294794.288000] usb 3-4: device descriptor read/64, error -32
[4294794.452000] usb 3-4: device descriptor read/64, error -32
[4294794.615000] usb 3-4: new high speed USB device using ehci_hcd and address 8
[4294794.678000] usb 3-4: device descriptor read/64, error -32
[4294794.842000] usb 3-4: device descriptor read/64, error -32
[4294795.005000] usb 3-4: new high speed USB device using ehci_hcd and address 9
[4294795.407000] usb 3-4: device not accepting address 9, error -32
[4294795.469000] usb 3-4: new high speed USB device using ehci_hcd and address 10
[4294795.871000] usb 3-4: device not accepting address 10, error -32

```

I can plug in a usb mouse directly and it works (luckily), but since this device works with the laptop, and works when I reboot the machine at the grub menu before ubuntu loads, there's something going on that I don't know how to solve in ubuntu.

Any ideas?

Thanks,
Brian

---

### Post by bhogg on 2006-09-14
Shortly after posting this I found the bug in the kernel:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54273](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54273)

I typed "rmmod ehci-hcd" and everything came back up.  Not sure how long this will last but hopefully it helps someone.

Anyone know why this is happening in the first place?

---

