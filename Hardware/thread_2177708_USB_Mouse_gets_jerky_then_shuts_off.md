---
title: "USB Mouse gets jerky then shuts off"
date: 2013-09-30
forum: Hardware
---

### Post by Botruckle on 2013-09-30
I'm using Ubuntu 13.04 64-bit, with the latest updates. In the past week or so, my Logitech wired mouse becomes jerky (pointer stops tracking, then jumps), then the mouse eventually shuts off. I checked the syslog and found that something called mtp-probe is looking at the device repeatedly. I've tried other USB ports with the same results (device number changes). The mouse was working fine, as near as I can remember, until about a week ago. I saw a similar problem on the AskUbuntu forum also with a Logitech mouse. 

Here is a clip from the syslog:

Sep 29 21:03:29 JW-PC mtp-probe: checking bus 8, device 3: "/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2"
Sep 29 21:03:29 JW-PC kernel: [106885.061976] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input108
Sep 29 21:03:29 JW-PC kernel: [106885.062346] hid-generic 0003:046D:C01D.0061: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0
Sep 29 21:03:29 JW-PC mtp-probe: bus: 8, device: 3 was not an MTP device
Sep 29 21:08:53 JW-PC kernel: [107208.592522] usb 8-2: input irq status -75 received
Sep 29 21:08:53 JW-PC kernel: [107208.644179] hub 8-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
Sep 29 21:08:53 JW-PC kernel: [107208.644186] usb 8-2: USB disconnect, device number 3
Sep 29 21:08:53 JW-PC kernel: [107208.900137] usb 8-2: new low-speed USB device number 4 using uhci_hcd
Sep 29 21:08:53 JW-PC kernel: [107209.084383] usb 8-2: New USB device found, idVendor=046d, idProduct=c01d
Sep 29 21:08:53 JW-PC kernel: [107209.084389] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 29 21:08:53 JW-PC kernel: [107209.084392] usb 8-2: Product: USB-PS/2 Optical Mouse
Sep 29 21:08:53 JW-PC kernel: [107209.084395] usb 8-2: Manufacturer: Logitech
Sep 29 21:08:53 JW-PC kernel: [107209.103572] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input109
Sep 29 21:08:53 JW-PC kernel: [107209.103805] hid-generic 0003:046D:C01D.0062: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.2-2/input0

Sep 29 21:08:53 JW-PC mtp-probe: checking bus 8, device 4: "/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2"
Sep 29 21:08:53 JW-PC mtp-probe: bus: 8, device: 4 was not an MTP device
Sep 29 21:10:53 JW-PC kernel: [107328.911894] usb 8-2: input irq status -75 received
Sep 29 21:10:54 JW-PC kernel: [107329.131514] hub 8-0:1.0: port 2 disabled by hub (EMI?), re-enabling...
Sep 29 21:10:54 JW-PC kernel: [107329.131522] usb 8-2: USB disconnect, device number 4
Sep 29 21:10:54 JW-PC kernel: [107329.375545] usb 8-2: new low-speed USB device number 5 using uhci_hcd
Sep 29 21:10:54 JW-PC kernel: [107329.551738] usb 8-2: New USB device found, idVendor=046d, idProduct=c01d
Sep 29 21:10:54 JW-PC kernel: [107329.551743] usb 8-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Sep 29 21:10:54 JW-PC kernel: [107329.551746] usb 8-2: Product: USB-PS/2 Optical Mouse
Sep 29 21:10:54 JW-PC kernel: [107329.551749] usb 8-2: Manufacturer: Logitech
Sep 29 21:10:54 JW-PC kernel: [107329.570961] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input110

---

### Post by Botruckle on 2013-10-15
Turns out that it was bad hardware after all. I replaced it with a new laser mouse and all has been well. Never had a mouse go bad on me before.

---

