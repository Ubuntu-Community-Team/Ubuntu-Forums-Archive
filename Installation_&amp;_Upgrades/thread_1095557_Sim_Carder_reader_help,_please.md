---
title: "Sim Carder reader help, please"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by DAllenSmith on 2009-03-13
I have a sim card reader, no company name was on the box the kernel log shows this:```
Mar 13 16:52:17 DasLap kernel: [92798.540080] usb 1-2: new full speed USB device using ohci_hcd and address 2
Mar 13 16:52:17 DasLap kernel: [92798.755294] usb 1-2: configuration #1 chosen from 1 choice
Mar 13 16:52:17 DasLap kernel: [92799.091398] usbcore: registered new interface driver usbserial
Mar 13 16:52:17 DasLap kernel: [92799.093865] usbserial: USB Serial support registered for generic
Mar 13 16:52:17 DasLap kernel: [92799.093969] usbcore: registered new interface driver usbserial_generic
Mar 13 16:52:17 DasLap kernel: [92799.093984] usbserial: USB Serial Driver core
Mar 13 16:52:17 DasLap kernel: [92799.100864] usbserial: USB Serial support registered for ark3116
Mar 13 16:52:17 DasLap kernel: [92799.100932] ark3116 1-2:1.0: ark3116 converter detected
Mar 13 16:52:17 DasLap kernel: [92799.177501] usb 1-2: ark3116 converter now attached to ttyUSB0
Mar 13 16:52:17 DasLap kernel: [92799.177560] usbcore: registered new interface driver ark3116
```
And the lsusb command shows this ```
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 6547:0232 Arkmicro Technologies Inc. ARK3116 Serial
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` i have found something in reference to this driver here: [http://manpages.ubuntu.com/manpages/intrepid/man4/uark.4freebsd.html]("http://manpages.ubuntu.com/manpages/intrepid/man4/uark.4freebsd.html") yes i have tried monosim and it does not work,  any help on making this thing work would be greatly appreciated**[B]**[/B]

---

### Post by DAllenSmith on 2009-03-14
bump

---

### Post by DAllenSmith on 2009-03-14
sigh...  bump

---

### Post by ConstintineVamp on 2009-11-27
Same problem... I have not a clue as to what We need to do to make this work, it may need a special software, or maybe just using commandline we may be able to access info on simcards... I have no clue on linux though......

---

