---
title: "USB keyboard - usb bus resets intermittently"
date: 2009-05-10
forum: Hardware
---

### Post by nixgeek on 2009-05-10
Hey All,

Recently my system seems to sporadically reset the usb bus. Keyboard and mouse are dead while the USB bus resets.

OS: Kubuntu 9.04 64bit

Comp specs:

Cpu: Intel i7 920
Mobo: Evga x58 sli
Video: Evga gtx 260
Mem: 12gb Corsair
HD: two 250 seagate {mirror OS}
HD: two 300 seagate {mirro /home}
PS: 700 watt Rockfish
KB: Logitech g15 {rev1}
Mouse: Logitech G5 {rev1}


Here are the errors from the syslog
===========================================================================
May 10 20:40:23 dadsgamer kernel: [260092.266928] usb 6-1.4: input irq status -75  received
May 10 20:40:23 dadsgamer kernel: [260092.384561] hub 6-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
May 10 20:40:23 dadsgamer kernel: [260092.384565] usb 6-1: USB disconnect, address 7
May 10 20:40:23 dadsgamer kernel: [260092.384566] usb 6-1.1: USB disconnect, address 8
May 10 20:40:23 dadsgamer kernel: [260092.429921] usb 6-1.4: USB disconnect, address 9
May 10 20:40:23 dadsgamer kernel: [260092.696059] usb 6-1: new full speed USB device using uhci_hcd and address 10
May 10 20:40:23 dadsgamer kernel: [260092.872037] usb 6-1: configuration #1 chosen from 1 choice
May 10 20:40:23 dadsgamer kernel: [260092.874980] hub 6-1:1.0: USB hub found
May 10 20:40:23 dadsgamer kernel: [260092.876950] hub 6-1:1.0: 4 ports detected
May 10 20:40:24 dadsgamer kernel: [260093.157954] usb 6-1.1: new low speed USB device using uhci_hcd and address 11
May 10 20:40:24 dadsgamer kernel: [260093.301018] usb 6-1.1: configuration #1 chosen from 1 choice
May 10 20:40:24 dadsgamer kernel: [260093.318107] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input11
May 10 20:40:24 dadsgamer kernel: [260093.344075] generic-usb 0003:046D:C221.0009: input,hidraw2: USB HID v1.10 Keyboard [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.0-1.1/input0
May 10 20:40:24 dadsgamer kernel: [260093.377861] input: Logitech Logitech Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.1/input/input12
May 10 20:40:24 dadsgamer kernel: [260093.404110] generic-usb 0003:046D:C221.000A: input,hiddev97,hidraw3: USB HID v1.10 Device [Logitech Logitech Gaming Keyboard] on usb-0000:00:1d.0-1.1/input1
May 10 20:40:24 dadsgamer kernel: [260093.485979] usb 6-1.4: new full speed USB device using uhci_hcd and address 12
May 10 20:40:24 dadsgamer kernel: [260093.634028] usb 6-1.4: configuration #1 chosen from 1 choice
May 10 20:40:24 dadsgamer kernel: [260093.643035] input: G15 Keyboard G15 Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.4/6-1.4:1.0/input/input13
May 10 20:40:24 dadsgamer kernel: [260093.672098] generic-usb 0003:046D:C222.000B: input,hiddev98,hidraw4: USB HID v1.11 Keypad [G15 Keyboard G15 Keyboard] on usb-0000:00:1d.0-1.4/input0
===========================================================================


This seems to be the error: [COLOR="Navy"]usb 6-1.4: input irq status -75  received[/COLOR]

Any ideas?

---

