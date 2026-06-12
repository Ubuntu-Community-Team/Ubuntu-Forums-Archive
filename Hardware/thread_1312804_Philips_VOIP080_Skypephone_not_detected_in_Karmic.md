---
title: "Philips VOIP080 Skypephone not detected in Karmic"
date: 2009-11-03
forum: Hardware
---

### Post by Sealbhach on 2009-11-03
It used to be just plug and play in Intrepid and Jaunty, an icon would show up on the desktop and I could select it from within Skype as my sound device. This has not happened in Karmic.

It shows up in lsusb and dmesg, so how do I get it to show up in Nautilus? If anyone could help I would be very grateful, I need my cheap Skype calls.

```
sealbhach@vaio-karmic:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c047 Logitech, Inc. Laser Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0471:1144 Philips 
```

```
sealbhach@vaio-karmic:~$ dmesg | grep usb
[    1.154977] usbcore: registered new interface driver usbfs
[    1.154977] usbcore: registered new interface driver hub
[    1.154977] usbcore: registered new device driver usb
[    2.730086] usb usb1: configuration #1 chosen from 1 choice
[    2.750082] usb usb2: configuration #1 chosen from 1 choice
[    2.750440] usb usb3: configuration #1 chosen from 1 choice
[    2.750725] usb usb4: configuration #1 chosen from 1 choice
[    2.750990] usb usb5: configuration #1 chosen from 1 choice
[    2.751257] usb usb6: configuration #1 chosen from 1 choice
[    2.751517] usb usb7: configuration #1 chosen from 1 choice
[    3.050075] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    3.203980] usb 1-2: configuration #1 chosen from 1 choice
[    3.780066] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    3.960016] usb 5-2: configuration #1 chosen from 1 choice
[    4.240070] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    4.411291] usb 6-1: configuration #1 chosen from 1 choice
[    4.690066] usb 7-1: new full speed USB device using uhci_hcd and address 2
[    4.870539] usb 7-1: configuration #1 chosen from 1 choice
[    5.164862] usb 7-1.1: new full speed USB device using uhci_hcd and address 3
[    5.210875] usbcore: registered new interface driver hiddev
[    5.225299] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input4
[    5.225386] generic-usb 0003:046D:C047.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.0-2/input0[B]
[    5.229336] input: PHILIPS PHILIPS VOIP080 as /devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.3/input/input5
[    5.229406] generic-usb 0003:0471:1144.0002: input,hidraw1: USB HID v1.00 Device [PHILIPS PHILIPS VOIP080] on usb-0000:00:1d.1-1/input3[/B]
[    5.229441] usbcore: registered new interface driver usbhid
```

---

### Post by Sealbhach on 2009-11-04
*bump*

anyone else use this Skypephone?

.

---

### Post by vfontanela on 2009-11-16
I do, I'm having the same problem. The same results with lsusb and dmesg and I really need to have this working. Any help would be apreciated.

PS: It worked nice in Jaunty.

---

### Post by Sealbhach on 2009-11-19
> **vfontanela said:**
> I do, I'm having the same problem. The same results with lsusb and dmesg and I really need to have this working. Any help would be apreciated.

PS: It worked nice in Jaunty.

I went back to Jaunty. Works fine there. I've filed a bug report on Launchpad. 

.

---

