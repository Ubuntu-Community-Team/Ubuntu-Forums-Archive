---
title: "SD card not mounting in 10.04"
date: 2010-07-03
forum: Hardware
---

### Post by SirPecanGum on 2010-07-03
I have two SD cards and two cameras. One SD card works fine in both cameras and Windows and Ubuntu. The other card works fine in both cameras and Windows but not Ubuntu - unless it is inserted before boot. Any ideas?

---

### Post by DonnyDonNothin on 2010-07-15
are you trying to read the card straight off the camera, usb, or from internal card reader? i have a similar problem with the internal reader on my laptop. its not instantly obvious, instead of using the "safely remove drive" use the eject option on ubuntu 10.04

---

### Post by Veloteuton63 on 2010-09-02
> **DonnyDonNothin said:**
> are you trying to read the card straight off the camera, usb, or from internal card reader? i have a similar problem with the internal reader on my laptop. its not instantly obvious, instead of using the "safely remove drive" use the eject option on ubuntu 10.04

Same problem here: The SD card is mounted when inserted at boot time.
The SD card is not mounted when inserted after boot
The SD card is read when interfaced directly through the camera (usb interface

Computer: HP Pavillon DV6 
lsusb:
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07ca:a309 AVerMedia Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a127 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by lavezarez on 2010-09-10
same problem here. ubuntu 10.04 does not recognize my internal card reader with SDcard inserted BEFORE or AFTER power-up.

---

