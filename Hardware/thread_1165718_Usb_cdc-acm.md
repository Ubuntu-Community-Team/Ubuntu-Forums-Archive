---
title: "Usb cdc-acm"
date: 2009-05-20
forum: Hardware
---

### Post by Jacob Christ on 2009-05-20
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
 
I've build my own USB CDC-ACM device (which hasn't passed any compliance tests of any such kind) and when it works when I plug it in, the first few times, but after a usually about the third to fifth time of plugging it in it will no longer be recognized.

The same device seems to work fine on my co-workers system running Gentoo w/ Linux 2.6.29

At this point I'm hoping that this is just a kernel issue and will be resolved when the kernel is upgraded, but I don't know how to tell if it is.

Jacob Christ

[11815.556105] usb 1-3.6: new full speed USB device using ehci_hcd and address 5
[11815.661029] usb 1-3.6: configuration #1 chosen from 1 choice
[11815.689895] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[11815.689919] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[11815.690417] usbcore: registered new interface driver cdc_acm
[11815.690420] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[14816.450691] usb 1-3.6: USB disconnect, address 5
[14818.440072] usb 1-3.6: new full speed USB device using ehci_hcd and address 6
[14818.539120] usb 1-3.6: configuration #1 chosen from 1 choice
[14818.539484] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14818.539501] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14830.274736] usb 1-3.6: USB disconnect, address 6
[14832.776129] usb 1-3.6: new full speed USB device using ehci_hcd and address 7
[14832.876900] usb 1-3.6: configuration #1 chosen from 1 choice
[14832.877288] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14832.877306] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14845.122784] usb 1-3.6: USB disconnect, address 7
[14847.368676] usb 1-3.6: new full speed USB device using ehci_hcd and address 8
[14847.467310] usb 1-3.6: configuration #1 chosen from 1 choice
[14847.467711] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14847.467730] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14855.362820] usb 1-3.6: USB disconnect, address 8
[14857.352083] usb 1-3.6: new full speed USB device using ehci_hcd and address 9
[14857.452018] usb 1-3.6: configuration #1 chosen from 1 choice
[14857.452248] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14857.452267] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14865.858855] usb 1-3.6: USB disconnect, address 9
[14868.104622] usb 1-3.6: new full speed USB device using ehci_hcd and address 10
[14868.204549] usb 1-3.6: configuration #1 chosen from 1 choice
[14868.204899] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14868.204916] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14877.122892] usb 1-3.6: USB disconnect, address 10
[14879.368157] usb 1-3.6: new full speed USB device using ehci_hcd and address 11
[14879.467576] usb 1-3.6: configuration #1 chosen from 1 choice
[14879.468410] cdc_acm 1-3.6:1.0: This device cannot do calls on its own. It is no modem.
[14879.468428] cdc_acm 1-3.6:1.0: ttyACM0: USB ACM device
[14887.618926] usb 1-3.6: USB disconnect, address 11
[14889.608191] usb 1-3.6: new full speed USB device using ehci_hcd and address 12
[14904.680115] usb 1-3.6: device descriptor read/64, error -110

---

### Post by Jacob Christ on 2009-05-21
I just built a new kernel from the Ubuntu repository which is only up to 2.6.28-12 and the problem persists.  I'm afraid I'm probably not skilled enough to merge the code from kernel.org into the build (at this time).

Jacob

---

