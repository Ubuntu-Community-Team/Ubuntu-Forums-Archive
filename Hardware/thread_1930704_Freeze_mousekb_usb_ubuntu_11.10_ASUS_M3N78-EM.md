---
title: "Freeze mouse/kb usb ubuntu 11.10 ASUS M3N78-EM"
date: 2012-02-24
forum: Hardware
---

### Post by odoricof on 2012-02-24
Hello everyone, I need some help groped to solve a problem:
I assembled a PC on a motherboard ASUS M3N78-EM and randomly stop working or USB keyboard or mouse, or both. I did several tests with negative results, I reinstalled ubuntu from scratch but the problem always reappears, then I tried to connect a keyboard to the PS2 and this always works even when the USB is locked. At this point I have concentrated on the USB ports, and I noticed that if removal and installation of the receiver usb keyboard stops working systematically until the next reboot.
During the block, if I type lsusb in a terminal lists the devices even if the unlink:

flavio @ mediacenter: ~ $ lsusb
Bus 001 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15c2: 0038 VFD Display SoundGraph Inc. GD01 MX / IR Receiver
Bus 004 Device 002: ID 045th: 0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth

In another partition windows 7 is that it works perfectly ...

Trying again I was able to eliminate the problem by disabling the option in the bios ACPI APIC.
With this disabled, the mouse never stop, if detachment / reattachment usb receiver continues to operate without problems ..
BUT ....
Ubuntu detects and runs one of the three core CPU AMD Phenom X3
I ask for help!

P.S. attached syslog

thanks

---

### Post by ThecaTTony on 2012-03-10
Hi, there is a problem related to nForce USB controller. I have the same motherboard but with ArchLinux running, and the problem is present to.

Some related info in the nvidia forums:
```
http://forums.nvidia.com/index.php?showtopic=96463
```

A workaround is buy an USB PCI card, and connect mouse and keyboard there.

Just to know, what option you disable in BIOS setup?

---

