---
title: "Creative Zen Vision M Freezes Upon Connection to Computer"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by hielscher on 2007-08-12
Hi all,

I just bought a 60GB Creative Zen VIsion M, and I'm having trouble getting it to work with any of the 3 Kubuntu boxes I have (one desktop, two laptops).  Whenever I connect the device via the USB cable to any of the three boxes, the zen hard freezes and I have to reset it.  This means I can't charge it via my Kubuntu boxes nor manage files.

Any ideas?  The one bit of output I have is from dmesg | grep usb:

[  832.892000] usb 5-7: device not accepting address 10, error -110
[ 1153.408000] usb 5-7: new high speed USB device using ehci_hcd and address 11
[ 1153.540000] usb 5-7: configuration #1 chosen from 1 choice
[ 1158.540000] usb 5-7: can't set config #1, error -110
[ 1159.468000] usb 5-7: USB disconnect, address 11
[ 4099.240000] usb 5-8: new high speed USB device using ehci_hcd and address 12
[ 4099.376000] usb 5-8: configuration #1 chosen from 1 choice
[ 4104.376000] usb 5-8: can't set config #1, error -110
[ 4105.604000] usb 5-8: usbfs: USBDEVFS_CONTROL failed cmd gnomad2 rqt 128 rq 6 len 1024 ret -110
[ 4235.952000] usb 5-8: USB disconnect, address 12

I've gone through the walkthroughs as to how to install gnomad2 and libmtp, but they don't help with this issue...

---

### Post by drewcoon on 2007-12-25
Try updating to the latest Zen Vision M firmware, I had the exact same problem as you on Gutsy (using my 60gb Vision M), I upgraded the firmware and now it works perfectly with gnomad2. Apparently the new firmware is quite a bit more stable.

You might need to hook it up to a Windows machine though (to update it), if it keeps freezing on you :)

---

