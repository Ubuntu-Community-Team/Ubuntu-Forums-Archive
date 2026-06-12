---
title: "Ext hard disk usb 2.0 doesn't work (infinite loop)"
date: 2008-08-17
forum: Hardware
---

### Post by grigio on 2008-08-17
```
[  156.112410] usb 6-3: new high speed USB device using ehci_hcd and address 76
[  156.230679] usb 6-3: configuration #1 chosen from 1 choice
[  156.264064] scsi75 : SCSI emulation for USB Mass Storage devices
[  156.268421] usb-storage: device found at 76
[  156.269743] usb-storage: waiting for device to settle before scanning
[  156.491545] usb 6-3: USB disconnect, address 76
[  157.696623] usb 6-3: new high speed USB device using ehci_hcd and address 77
```
LOOP(..)

It's the same with Hardy or Intrepid Kernel  :(

If I plug it on usb 1.0 ports it works, but it is very slow

[~]$ lsusb
Bus 006 Device 009: ID 0766:0001 Jess-Link Products Co., Ltd

---

### Post by finito on 2008-08-17
Yes I used to get that on my USB hub sometimes, I upgraded to a powered USB HUB and I never saw that error. if you are using a hub, try plugging it in directly, if you have plugged it directly than it could be that the port you have is bad. 

I have a PC at work where I used a cheap power Supply with a lot of USB stuff attached to it and most of the USB port Died. anyway just try another port.

---

### Post by grigio on 2008-08-17
I don't have and hub. It's a usb 2.0 PCI card

---

### Post by finito on 2008-08-17
Ok I am guessing you have a old computer that has USB 1.0 Ports (On which the drive works, correct?) that why you are using the USB 2.0 PCI card. In that case have you tried the Drive on another computer, I am guessing you did and it worked. Can you check the PCI card on another computer handy.

---

### Post by grigio on 2008-08-19
I did some tests and the conclusion is that my usb2 ports doesn't support self powered external hds

---

