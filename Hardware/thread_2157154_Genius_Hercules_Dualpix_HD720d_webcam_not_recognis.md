---
title: "Genius Hercules Dualpix HD720d webcam not recognised in Ubuntu 12.10"
date: 2013-06-24
forum: Hardware
---

### Post by Mokdeabar on 2013-06-24
Hey all,

I've searched for this, but could not find a fix everywhere. I was given a Genius Hercules Dualpix HD720d webcam, however it is not working on my Ubuntu 12.10 machine. 

When I plug it in, it lights up, so there's definitely a connection, but even Cheese brings the message "No Device Found" which I've never had when I connect any other webcam before. I really do not want to have to buy another webcam, so if someone could help me fix this, it would be greatly appreciated!

If you would like me to provide you with any results from the terminal, just let me know what to type and I'll respond asap.

---

### Post by Mokdeabar on 2013-06-25
No pointers? :(

---

### Post by gordintoronto on 2013-06-26
lsusb

It should produce several lines of output, including one which looks like this:
Bus 003 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

The interesting part is "0ac8:303b". Plug that into Google along with some other words such as linux, solved, webcam, usb.

---

### Post by Mokdeabar on 2013-06-26
Thanks for the response... I ran lsusb and got the following:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 006 Device 002: ID 046d:c317 Logitech, Inc. Wave Corded Keyboard
Bus 006 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 002: ID 0a5c:200a Broadcom Corp. BCM2035 Bluetooth dongle
Bus 002 Device 008: ID 04fc:0801 Sunplus Technology Co., Ltd 
Bus 006 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 006 Device 006: ID 093a:2628 Pixart Imaging, Inc. 
Bus 002 Device 026: ID 0bb4:0ffe High Tech Computer Corp. Desire HD (modem mode)


I'm guessing the "Bus 006 Device 006: ID 093a:2628 Pixart Imaging, Inc." one is the one you're talking about... so I searched Google for "093a:2628" and still can't find a solution for it :(

---

### Post by gordintoronto on 2013-06-26
It appears that is a V4L2 webcam, which is supported in gspca. I found too many references to chase them all, when I Googled: 093a:2628 linux

---

