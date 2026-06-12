---
title: "How to test GPS receiver"
date: 2011-07-29
forum: Hardware
---

### Post by matrix72 on 2011-07-29
Hi all.

I have problem testing my GPS receiver (BR-355) that are connected to a usb port via a USB-Serial adapter (PL-2303). I've have tried to test the GPS-receiver using Viking and Ubuntu v. 9.10. But it seems that it cannot detect any GPS-receiver, although running the command **dmesg** shows that pl2303 is attached to /dev/ttyUSB0. 

Can anyone please provide a step by step instruction on how I can communicate with my gps-receiver. Also if there is a good tool for testing the functioning of the gps and/or serial/usb port please let me know.

Furthermore, I am wondering when the gps-receiver is connected through a usb-serial cable, if writing code for communicating with the gsp-receiver, using java for example, should I use a javax.comm API (serial) or javax.usb API (also called JSR80). 

Regards

V. Pham

---

### Post by sanderj on 2011-07-29
My method with unknown USB-devices: 

Run 'lsusb' twice: once with the USB-device not connected, once with the USB-device connected. The extra line is the ID of the USB-device. Post that line here, and Google for it.

And post the relevant output of dmesg and/or /var/log/messages here.

Oh, and run the most recent Ubuntu version, so 11.04. As you seem to use Ubuntu 9.10, you could run 11.04 from a live CD/USB-stick (no need to install).

---

### Post by matrix72 on 2011-08-03
Hi.

Here is the output of lsusb.

lsusb without gps-receiver:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 002: ID 049f:0051 Compaq Computer Corp. KU-0133 Easy Access Interner Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsusb with gps-receiver:

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 003 Device 002: ID 049f:0051 Compaq Computer Corp. KU-0133 Easy Access Interner Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The difference is the following line:

Bus 007 Device 002: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port

---

### Post by sanderj on 2011-08-03
And did you Google "067b:2303 Prolific Technology, Inc. PL2303 Serial Port" & Linux & GPS (all in one search command)?

---

### Post by victor1234 on 2011-08-03
All GPS units require a certain amount of time to acquire 4 	satellites, the minimum number needed for fixing a position 	(3 for space, 1 for time).  Most GPS receivers implement tracking 	in a reduced power mode that enables fixes to be computed 	very rapidly when switched to a fully alert state.  For the 	LeadTek 9546, test was performed to investigate the acquisition 	times necessary for a sequence of cold starts.

---

