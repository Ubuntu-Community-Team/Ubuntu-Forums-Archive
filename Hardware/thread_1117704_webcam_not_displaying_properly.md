---
title: "webcam not displaying properly"
date: 2009-04-06
forum: Hardware
---

### Post by matt_30 on 2009-04-06
when plugging in my webcam it is detected but this is what i get out of the webcam.

[IMG]http://i664.photobucket.com/albums/vv5/matt_30/webcam.jpg[/IMG]

here is my lsusb:

```

matt@matt-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 003: ID 045e:00bd Microsoft Corp. Fingerprint Reader
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The ViewQuest Technologies, Inc. CS330 WebCam is the one i have been trying to set up. i have also tried a creative webcam vista and i get the same output.

many thanks

matt.

---

### Post by LuxVoodoo on 2009-04-06
I am having the very same trouble in both the Intrepid and Jaunty releases of Ubuntu.  The closest I've ever come to getting it right is a test pattern and that's about it.  But I pretty much have the same display issues as the original poster, no matter what cam software I use. This camera did work fine with Cheese under Hardy, so something broke along the way.  Here is my lsusb:

```
rich@rich-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0733:0401 ViewQuest Technologies, Inc. CS330 WebCam
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
rich@rich-desktop:~$
```

I am using the same cam and model number as the original poster. Although the manufacturer label on the cam says Intel.

---

### Post by matt_30 on 2009-04-06
yes it is an intel webcam using the viewquest driver it worked fine under hardy for me too

---

