---
title: "Chicony Twinkle Cam Pro"
date: 2007-10-01
forum: Hardware &amp; Laptops
---

### Post by porcellinux on 2007-10-01
Hi everyone! It's a while that I have being trying to set up my webcam Chicony Twinkle Cam Pro. I found out that ov511 is supporting it.

I installed the paket ov511, and made a  $ sudo modprobe ov511,but nothing happenes, when I open CAMORAMA it says: "impossible to connect to video device /dev/video0".

I created /dev/video0 by a $ mknod /dev/video0 c 81 0  and by a $ chmod 666 /dev/video0

but nothing works

the output of $ lsusb is the following::

Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 010: ID 03f0:3a02 Hewlett-Packard
Bus 004 Device 011: ID 03f0:2305 Hewlett-Packard ScanJet 3970c
Bus 004 Device 009: ID 05e3:0606 Genesys Logic, Inc.
Bus 004 Device 008: ID 05e3:0606 Genesys Logic, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 002 Device 002: ID 05a9:8519 OmniVision Technologies, Inc.

Dove OmniVision Technologies, Inc. is my WebCam.
I tryed also EasyCam and EasyWebCam, but it crashes.
What can I do?? the ov511 website says Chicony Twinkle Cam Pro is fully supported and working!!  ([http://ovcam.org/ov511/cameras.html](http://ovcam.org/ov511/cameras.html))

Thanks!

---

