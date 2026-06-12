---
title: "HP Webcam 04f2:b016 supported, but not working!"
date: 2009-01-18
forum: Hardware
---

### Post by looi76 on 2009-01-18
Hi, I have found out that my webcam is supported by Ubuntu thought [UVC]("http://linux-uvc.berlios.de/").

```
looi76@looi76-laptop:~$ lsusb
**Bus 007 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd **
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
looi76@looi76-laptop:~$ 

```

I have downloaded and install their latest driver but still the webcam doesn't work! I have tired to make it work on cheese. need help!

---

### Post by looi76 on 2009-01-23
It has been 5 Days! I'm sure someone in this forum can help me... :)

---

### Post by WarrenSensei on 2013-01-20
*bump*
This is my case as well, has been for a while. ](*,)
If I run Cheese, the webcam's light comes on, but cheese doesn't get an image. Sometimes I will get very poor, low frame rate video for a few seconds, then a frozen image.
It worked *fine* under 10.*, but went *poof* when I updated to 11.04 and has never really worked again, despite trying again each upgrade. I'm now running the current 12.10, and I can sometimes get my Logitech USB webcam to work, but only sometimes.

lsusb returns:
> Bus 001 Device 004: ID 04f2:b053 Chicony Electronics Co., Ltd #this is my built-in webcam
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. AES2810
Bus 008 Device 002: ID 046d:08d7 Logitech, Inc. QuickCam Communicate STX #this is my USB webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


After installing guvcview (which I hadn't realized I hadn't reinstalled after a rocky update to 12.10), guvcview can see my USB cam, but still not the internal, but now Cheese **can** see both. Go figure.

In either case, nothing is being sent to my browser for use in any web chat environment.

Anyone know what even *might* be going on?

---

