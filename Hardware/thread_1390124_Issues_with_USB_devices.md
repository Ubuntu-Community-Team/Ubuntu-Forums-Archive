---
title: "Issues with USB devices"
date: 2010-01-25
forum: Hardware
---

### Post by Romualdou on 2010-01-25
Hi there,

following issue : USB devices, like mouse, USB sticks, SD card from the integrated card reader work just fine after startup. But after a while,, new devices plugged in will not be recognized anymore. Need to reboot to get things working back again. 

This is a main issue when I decide to plug in my mouse on my laptop after a while and see I should reboot to have it working. Same thing with my scanner....

Any idea how to solve this or at lease reactivate devices detection without rebooting ?

BTW : lsusb shows the devices properly. 

Hardware : Samsung R522 + all kind of USB peripherals. 
Ubuntu : 9.10

~$ lsusb
**Bus 003 Device 002: ID 046d:c062 Logitech, Inc. **
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0ac8:c335 Z-Star Microelectronics Corp. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

In this example, the mouse doesn't work, while the built-in webcam works just fine, as it was already plugged in on boot (obviously...)

Googling around showed 2 options : either reboot or kernel downgrade which I consider is a joke : hot plugin from USB devices must be a standard !

Any idea how to come forward here ? :confused:

---

