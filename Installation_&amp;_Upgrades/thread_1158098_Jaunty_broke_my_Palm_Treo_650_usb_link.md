---
title: "Jaunty broke my Palm Treo 650 usb link"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by geoffatmk on 2009-05-13
Hi

I have happily synchronised my Treo 650 for some time now with evolution using a usb link.

I recently installed Jaunty and it seems to have broken the connection.

When connected and trying to link, the plam generates the folowing in lsusb;

gjj@samson:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:200a Broadcom Corp. Bluetooth dongle
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 012: ID 0830:0061 Palm, Inc. Lifedrive / Treo 650/680 / Tunsten E2/T5/TX / Zire 21/31/72 / Z22
Bus 002 Device 003: ID 0461:4d04 Primax Electronics, Ltd Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

So it is being recognised but it is not telling me what I have to point to to make the software and Treo connect.

Historically I have used /dev/pilot but the message I get now is;

Failed to connect using device "Cradle" on port /dev/pilot  Check your configuration as you requested old-style usbserial "ttyUSB" synching but do not have the USB "visor" kernel loaded.  You may need to select a usb device.

I have tried all the devices listed but ge the smae error every time.  I have never messed with the kernel and cannot believe that Jaunty has not been set up to link to Palm devices so can someone guide me in what I have to do to get it to work again please?


Geoff

---

