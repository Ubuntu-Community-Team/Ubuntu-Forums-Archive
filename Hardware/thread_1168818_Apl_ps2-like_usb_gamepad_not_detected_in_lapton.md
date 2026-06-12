---
title: "Apl ps2-like usb gamepad not detected in lapton"
date: 2009-05-24
forum: Hardware
---

### Post by atundel on 2009-05-24
Hey people:

I have a generical APL PS2-like USB Gamepad. 

It is not detected at all on my jaunty laptop (it doesn't even show /dev/input/js0), but it works totally on my desktop computer which also uses linux.

Here are my dmesg's

For the laptop:
$dmesg
[ 1309.184170] usb 7-1: new low speed USB device using uhci_hcd and address 9
[ 1309.364409] usb 7-1: configuration #1 chosen from 1 choice

$lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 009: ID 0079:0006  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 04f3:0210 Elan Microelectronics Corp. AM-400 Hama Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ac8:c302 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 0d49:7410 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


For the desktop computer:

$dmesg
...
[  135.557578] input: DragonRise Inc.   Generic   USB  Joystick   as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input7
[  135.572144] generic-usb 0003:0079:0006.0002: input,hidraw0: USB HID v1.10 Joystick [DragonRise Inc.   Generic   USB  Joystick  ] on usb-0000:00:1d.3-1/input0


Thanks in advance!!!

---

### Post by Super TWiT on 2009-05-24
What Linux does your desktop run?  Also, have you tried another usb port?

---

### Post by atundel on 2009-05-24
The both used Jaunty, but I realised it works on my laptop when I use the 2.6.28-11-generic kernel, instead of 2.6.30, which I use because of the graphic card's controller.
Now it seems to work properly :)

---

### Post by atundel on 2009-05-25
[  197.496162] usb 3-1: new low speed USB device using uhci_hcd and address 2
[  197.670007] usb 3-1: configuration #1 chosen from 1 choice


After the preious message, while I was playing happily, it started working on the laptop with 2.6.28 kernel

Can anyone help me???

---

