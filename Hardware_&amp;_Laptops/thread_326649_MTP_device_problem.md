---
title: "MTP device problem"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by skiani on 2006-12-27
Hi,

I'm having problems getting an MP3 player to work properly (the device is a Sansa M240) under MTP (LibMTP) control. When I hook the device up Ubuntu sees it as a USB disk and mounts it. This would be fine but the files stored as through MTP on windows, nor can windows see the files stored by mounting on Linux. Here's the message get from libmtp:

[INDENT]$ mtp-detect
Found non-autodetected device "SanDisk Sansa m240" on USB bus...
usb_claim_interface(): Device or resource busy
Connection error.
No devices.[/INDENT]

Other MTP devices I have played with are not USB mountable so I wonder if this is a bug with libmtp/hotplug not letting MTP view  the device? Any suggestions? Thanks.

---

### Post by SZF2001 on 2007-01-01
You have to switch the player to MSC mode if you don't want to put up with MTC bullcrap.

[http://www.ubuntuforums.org/showthread.php?t=312196](http://www.ubuntuforums.org/showthread.php?t=312196) <--- A Sansa guide

---

