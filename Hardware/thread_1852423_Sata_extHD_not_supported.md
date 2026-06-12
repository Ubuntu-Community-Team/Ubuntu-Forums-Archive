---
title: "Sata extHD not supported"
date: 2011-09-30
forum: Hardware
---

### Post by vanhecke on 2011-09-30
Hi,

I have a new Seagate ST91000640NS S-ATA HD, which I've put in an Ice Box USB 3 case, But my computer cannot mount it properly. These are the symptoms:

- Disk utility detects an interface (ASMT 2105) and a device (at /dev/sde), with a connection of 480 Mb/s
- The SMART status says "not supported"
- Capacity says "no media detected"
- fdisk /dev/sde/ gives "Unable to open /dev/sde"


Formatting is also not possible (no medium found).

My USB ports are USB 2, but I understood USB3 is backwards compatible. Furthermore, I replaced the HD with an older S ATA in the same Ice Boy, which works fine. This rules out the Ice box interface.
lsusb output:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 003 Device 003: ID 0461:4d81 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 020: ID 1058:1021 Western Digital Technologies, Inc. 
Bus 002 Device 019: ID 07ab:fcfe Freecom Technologies 
Bus 002 Device 018: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



What am I doing wrong?


Any help very welcome!
(system: Natty 11.04, Linux 2.6.38-11)

---

