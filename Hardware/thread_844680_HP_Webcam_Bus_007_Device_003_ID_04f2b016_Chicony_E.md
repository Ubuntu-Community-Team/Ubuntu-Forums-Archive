---
title: "HP Webcam Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd"
date: 2008-06-29
forum: Hardware
---

### Post by starcannon on 2008-06-29
I am attempting to get the internal usb webcam that shipped with this hp pavilion dv2600 working.

I will be collecting information and posting it here for others to make of it what they can, and with luck perhaps we can eventually mark this thread as solved.

The camera shows up using lsusb as:

```
Bus 007 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
```

Some Links about this camera:
[http://sidux.com/PNphpBB2-viewtopic-t-11152-newlang-rus.html](http://sidux.com/PNphpBB2-viewtopic-t-11152-newlang-rus.html)

---

### Post by MatMan on 2009-01-25
Did you ever solve this? I have the same leptop and am about to try  to. Any hints?

---

### Post by jcoppala on 2009-01-25
Hi 
I have the HP Pavilion dv2707TX running Ubuntu 8.10, I have the some webcam

coppala@deus-machina:~$ lsusb
Bus 007 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

and is working fine... skype cheese ucview 

what OS are u running?

---

### Post by MatMan on 2009-01-25
I am running Intrepid ibex i386 i think. this my webcam. maybe it is working and I don't know how to use it?

mathew@vickersmatic:~$ lsusb
Bus 007 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mathew@vickersmatic:~$

---

