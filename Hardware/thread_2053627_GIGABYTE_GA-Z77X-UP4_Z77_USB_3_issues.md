---
title: "GIGABYTE GA-Z77X-UP4 Z77 USB 3 issues?"
date: 2012-09-05
forum: Hardware
---

### Post by rotten777 on 2012-09-05
I am having no luck getting some USB ports to work. I have plugged in my mouse into the back ports (directly on the motherboard, not the ones with the headers to the case's USB ports). It won't work. 

I get this in dmesg:

```
[376903.870198] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input12
[376903.870542] generic-usb 0003:046D:C069.0004: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.0-1.3/input0
[377962.034269] usb 5-1.1: new high-speed USB device number 23 using xhci_hcd
[377962.034435] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377962.237681] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377962.440941] usb 5-1.1: device not accepting address 23, error -22
[377962.512829] usb 5-1.1: new high-speed USB device number 24 using xhci_hcd
[377962.512960] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377962.716257] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377962.919545] usb 5-1.1: device not accepting address 24, error -22
[377962.991494] usb 5-1.1: new high-speed USB device number 25 using xhci_hcd
[377962.991681] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377963.194907] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377963.398162] usb 5-1.1: device not accepting address 25, error -22
[377963.470036] usb 5-1.1: new high-speed USB device number 26 using xhci_hcd
[377963.470191] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377963.673449] xhci_hcd 0000:63:00.0: Setup ERROR: address device command for slot 2.
[377963.876732] usb 5-1.1: device not accepting address 26, error -22
[377963.876853] hub 5-1:1.0: unable to enumerate USB device on port 1

```


Kernel is 3.2.0-30-generic. Same mouse (and two others) works when moved to front USB ports. Any ideas?

---

