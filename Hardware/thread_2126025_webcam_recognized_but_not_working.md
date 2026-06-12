---
title: "webcam recognized but not working"
date: 2013-03-15
forum: Hardware
---

### Post by doogiekd on 2013-03-15
friends, 
i have an old webcam that is recognized by cheese & skype but only a black screen appears. 

any thoughts if and/or how i can get this camera to work before i buy a new one?

thanks.

lsusb:
Bus 001 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 001 Device 003: ID 050d:0224 Belkin Components F5U224 USB 2.0 4-Port Hub
Bus 002 Device 002: ID 03f0:3312 Hewlett-Packard OfficeJet J6410
Bus 005 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
**Bus 001 Device 018: ID 0af9:0011 Hama, Inc. Micro Innovations IC50C Webcam**
Bus 001 Device 006: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 001 Device 007: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 001 Device 008: ID 0a5c:2154 Broadcom Corp.

---

### Post by papibe on 2013-03-15
Hi doogiekd.

Could you post the result of these commands?
```
lsb_release -a

uname -a

lsmod | grep -i gspca

```
Regards.

---

### Post by doogiekd on 2013-03-15
thanks for replying! i'm hoping that i don't have to buy a new webcam. here are the command results that you requested:

**lsb_release -a:**
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
[B]
uname -a:[/B]
Linux earth 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 18:26:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[B]
lsmod | grep -i gspca:[/B]
gspca_spca508          17342  0 
gspca_main             28323  1 gspca_spca508
videodev              120310  3 gspca_main,pwc,videobuf2_core

---

### Post by papibe on 2013-03-15
Thanks.

It looks like the correct driver is loaded.

Have you tried if it works under GUVCViewer?

Have you tried the LD_PRELOAD trick (see [here]("http://askubuntu.com/questions/176066/why-doesnt-ld-preload-v4l1compat-so-work-with-64-bit-skype"))?

Regards.

---

### Post by doogiekd on 2013-03-15
well it works under guvcviewer, but the pic is really bad. camera works well in windows 7. the preload trick did not work. time for a new webcam or any other suggestions? thanks.

---

### Post by papibe on 2013-03-15
Logitech webcams have been good to me.

Check this page with useful information: [Ubuntu Webcams]("https://help.ubuntu.com/community/Webcam"). I'd go with any camera with good UVC driver support.

Regards.

---

