---
title: "Canon Lide50 Scanner"
date: 2011-12-02
forum: Hardware
---

### Post by chaiwalla on 2011-12-02
My Lide50 scanner has stopped working after upgrading to 11.10.
lsusb shows it is connected.
andy@andy-P5K:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 005: ID 05e3:0607 Genesys Logic, Inc. 
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 006: ID 046d:0a0e Logitech, Inc. 
Bus 001 Device 008: ID 04a9:2213 Canon, Inc. CanoScan LiDE 50/LiDE 35/LiDE 40
----------
scanimage -T
libusb couldn't open USB device /dev/bus/usb/001/001: Permission denied.
libusb requires write access to USB device nodes.
   -----------

Can anybody help ?

---

### Post by bayvista on 2012-02-17
Same here. They must have dropped this off in the upgrade.

---

