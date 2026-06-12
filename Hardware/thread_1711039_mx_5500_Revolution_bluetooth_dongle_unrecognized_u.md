---
title: "mx 5500 Revolution bluetooth dongle unrecognized ubuntu 10.10"
date: 2011-03-20
forum: Hardware
---

### Post by pils92 on 2011-03-20
I recently did a fresh install of ubuntu 10.10 on my HTPC, I have a Logitech mx5500 wireless kb/mouse with a bluetooth usb adapter. The adapter still works in that I am typing this with it now, but the bluetooth functionality is gone. It does work in Ubuntu 10.04, here is my lsusb output.


luke@media-1:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c71c Logitech, Inc. 
Bus 003 Device 003: ID 046d:c71b Logitech, Inc. 
Bus 003 Device 002: ID 046d:0b06 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 147a:e03e Formosa Industrial Computing, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Ubuntu 10.04 was the same except there would have been a device 005, logitech bt receiver line...

How do I fix this?:confused:

---

### Post by pils92 on 2011-04-01
Any one got an idea?

---

### Post by pils92 on 2011-05-17
post removed by author

---

### Post by pils92 on 2011-05-17
lsusb for ubuntu 10.04 bluetooth is functional

pils92@pils92-pc:~$ lsusb
Bus 008 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 010: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 006 Device 009: ID 046d:c71c Logitech, Inc. 
Bus 006 Device 008: ID 046d:c71b Logitech, Inc. 
Bus 006 Device 007: ID 046d:0b06 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 1267:0103 Logic3 / SpectraVideo plc G-720 Keyboard
Bus 003 Device 003: ID 0a5c:2151 Broadcom Corp. 
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0c45:1677 Microdia 
Bus 001 Device 006: ID 03f0:5511 Hewlett-Packard DeskJet F300 series
Bus 001 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 004: ID 050d:0201 Belkin Components Peripheral Switch
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

see 4th line down from lsusb, line not shown in ubuntu 10.10 with same usb dongle. :confused:

---

