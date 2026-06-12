---
title: "Installing Poscope"
date: 2010-11-13
forum: Hardware
---

### Post by shaunarman on 2010-11-13
I hope that someone can help me out here. I have purchesed a PoScope basic2 and I am unable to get this to install in XP through VMware. I know that Ubuntu sees the device from using the lsusb command.
```

Bus 008 Device 006: ID 10c4:ea67 Cygnal Integrated Products, Inc. 
Bus 008 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
It is the first one listed. Windows even sees this through VMware, but is unable to install the driver. I would rather get this to work in Ubuntu, but would be satisfied using M$.
Please anyony help as I need this for my microprocessor class.

---

### Post by Tumblweed on 2010-11-30
WOW at least im not the only one having this problem You ever have any luck getting it working?
ken@ken-Studio-1737:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1410:6000 Novatel Wireless 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR=Red]Bus 005 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810[/COLOR]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 03f0:7f11 Hewlett-Packard 
Bus 002 Device 006: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 005: ID 1058:1110 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 0d49:7250 Maxtor 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:63fa Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ken@ken-Studio-1737:~$ 
Its there but I cant use it =(

---

