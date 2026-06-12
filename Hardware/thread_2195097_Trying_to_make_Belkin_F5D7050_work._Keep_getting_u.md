---
title: "Trying to make Belkin F5D7050 work. Keep getting usb 1-6: new high-speed USB device.."
date: 2013-12-22
forum: Hardware
---

### Post by leandrog.1 on 2013-12-22
Recently, I fresh installed Xubuntu 13.10 on my desktop. Since then I can't make the Belkin Wireless G USB Network Adaptor (F5D7050 v4) work. When I plug it in dmesg keeps producing these messages:
```

[ 1330.964011] usb 1-6: new high-speed USB device number 100 using ehci-pci
[ 1331.304014] usb 1-6: new high-speed USB device number 101 using ehci-pci
[ 1331.644012] usb 1-6: new high-speed USB device number 102 using ehci-pci
[ 1331.984012] usb 1-6: new high-speed USB device number 103 using ehci-pci
[ 1332.540012] usb 1-6: new high-speed USB device number 105 using ehci-pci
[ 1333.312011] usb 1-6: new high-speed USB device number 108 using ehci-pci
[ 1334.084011] usb 1-6: new high-speed USB device number 111 using ehci-pci

```
lsusb produces this:
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 008 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
So something is failing in between.
Also, when I try to reboot, the system stalls at some point until I pull out the adapter.
Finally, I checked the setup of the motherboard, and USB 2.0 is enabled at high speed. Anyway, I didn't change anything in the BIOS before the fresh installation.
I've tried different USB ports with no luck.
I've been looking on for a solution for days and I just couldn't find it.

---

