---
title: "usb hub full-speed vs high-speed"
date: 2012-06-07
forum: Hardware
---

### Post by mizar66 on 2012-06-07
On Precise, connecting a 4port usb hub I get:

```

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub

```and

```

dmesg
[  137.228102] usb 2-1: new full-speed USB device number 4 using uhci_hcd
[  137.409553] hub 2-1:1.0: USB hub found
[  137.411290] hub 2-1:1.0: 4 ports detected

```So it seems it is a 2.0 hub but it is recognised as a full-speed usb device and uses uhci instead of ehci.

What could be wrong? Is there a way to force the hub in high-speed mode?

TIA

---

### Post by jraftb on 2012-06-19
im owundering the same thing as im told this is why my mouse wont work, it shows as a 1.1 hub instead of a 2.0

---

