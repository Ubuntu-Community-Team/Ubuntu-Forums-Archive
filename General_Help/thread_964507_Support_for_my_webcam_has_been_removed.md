---
title: "Support for my webcam has been removed?"
date: 2008-10-31
forum: General Help
---

### Post by CShadowRun on 2008-10-31
I just updated to intrepid ibex, my webcam worked fine with no modification out of the box with hardy, now it does not work at all. Re-plugging it results in the following from dmesg

[ 2317.651962] usb 2-5: USB disconnect, address 3
[ 2321.380574] usb 2-5: new full speed USB device using ohci_hcd and address 7
[ 2321.600896] usb 2-5: configuration #1 chosen from 1 choice
[ 2321.603619] usb 2-5: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x303B)
[ 2321.723206] usb 2-5: No supported image sensor detected

Any ideas? I like my webcam :(

Edit: just wanted to say that on the whole ibex is awesome, love the pulseaudio wine + flash fix, the new gnome is kinda buggy with multiple X screens, but i'm gonna start bug reporting, so pretty good :D

---

### Post by CShadowRun on 2008-10-31
Used a liveCD to boot into hardy to get the dmesg from that, in hardy my webcam works and dmesg says

[  727.936399] usb 1-1: new full speed USB device using uhci_hcd and address 11
[  728.129679] usb 1-1: configuration #1 chosen from 1 choice
[  218.258814] usb 1-2: new full speed USB device using uhci_hcd and address 12
[  728.780994] usb 1-2: device descriptor read/64, error -71
[  728.900053] Linux video capture interface: v2.00
[  729.004761] usb 1-2: device descriptor read/64, error -71
[  729.220678] usb 1-2: new full speed USB device using uhci_hcd and address 13
[  729.344659] usb 1-2: device descriptor read/64, error -71
[  729.572608] usb 1-2: device descriptor read/64, error -71
[  729.788580] usb 1-2: new full speed USB device using uhci_hcd and address 14
[  730.196503] usb 1-2: device not accepting address 14, error -71
[  730.308486] usb 1-2: new full speed USB device using uhci_hcd and address 15
[  730.716406] usb 1-2: device not accepting address 15, error -71
[  730.716499] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[  219.445616] usbcore: registered new interface driver gspca
[  219.445624] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[  219.588194] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
[  219.588229] usbcore: registered new interface driver zc0301

---

### Post by CShadowRun on 2008-11-03
Still got this issue!

---

### Post by loell on 2008-11-03
what webcam application have you tried in ibex so far?

---

### Post by CShadowRun on 2008-11-04
Cheese, Adobe Flash Player, aMSN
All of them work in hardy

---

### Post by CShadowRun on 2008-11-05
Still got this problem :(

---

### Post by CShadowRun on 2008-11-08
Come on people, having to use virtualbox's usb passthrough to windows XP for anything i want to do with my webcam :(

---

