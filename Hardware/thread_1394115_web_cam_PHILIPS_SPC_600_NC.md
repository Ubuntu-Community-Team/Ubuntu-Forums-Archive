---
title: "web cam PHILIPS SPC 600 NC"
date: 2010-01-30
forum: Hardware
---

### Post by slakov on 2010-01-30
Hi! I have a problem using my web cam in Ubuntu. After plugging it into USB the camera's indicator switches on. 

dmesg gives the following output:

[ 8699.780090] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 8699.983249] usb 5-1: configuration #1 chosen from 1 choice
[ 8700.102968] Linux video capture interface: v2.00
[ 8700.181450] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[ 8700.183139] usb 5-1: SN9C105 PC Camera Controller detected (vid:pid 0x0471:0x0327)
[ 8700.318155] usb 5-1: No supported image sensor detected for this bridge
[ 8700.318239] usbcore: registered new interface driver sn9c102
[ 8700.375861] usbcore: registered new interface driver snd-usb-audio


But no application see the cam. Any suggestions? 

Many thanks upfront!

---

