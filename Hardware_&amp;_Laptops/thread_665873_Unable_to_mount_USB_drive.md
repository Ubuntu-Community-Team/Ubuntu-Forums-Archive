---
title: "Unable to mount USB drive"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by Mujaheiden on 2008-01-12
An external usb harddrive, a 2,5" argosy hd 260 won't mount on my IBM R32 thinkpad.

```
$ dmesg | tail
[  721.472000] usb 2-2: device descriptor read/64, error -71
[  721.696000] usb 2-2: device descriptor read/64, error -71
[  721.912000] usb 2-2: new full speed USB device using uhci_hcd and address 100
[  722.032000] usb 2-2: device descriptor read/64, error -71
[  722.256000] usb 2-2: device descriptor read/64, error -71
[  722.472000] usb 2-2: new full speed USB device using uhci_hcd and address 101
[  722.880000] usb 2-2: device not accepting address 101, error -71
[  722.992000] usb 2-2: new full speed USB device using uhci_hcd and address 102
[  723.400000] usb 2-2: device not accepting address 102, error -71
[  723.400000] hub 2-0:1.0: over-current change on port 2
```and

```
$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 013: ID 0840:0084 Argosy Research, Inc. 
Bus 002 Device 002: ID 046d:c018 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```I think its something with the over-current change on port 2. The hard drive makes some clicking noises; it looks like its trying to get up to speed. For Windows, Im supposed to install the USB Host controller.

Any tips?

---

