---
title: "Usb Webcam Help"
date: 2008-08-08
forum: Hardware
---

### Post by Delirium_Trigger on 2008-08-08
I currently use the HP 2.0 (NX-6000) USB Webcam.
My problem is that Ubuntu isn't even recognizing the webcam.
I went to the HP website and their drivers only work for Windows and OS X.
Is there any way to get the drivers to work with Hardy?

Here are the results of lsusb

```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 15b8:6002  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

I am running Hardy on a Toshiba Satellite A205-S5831.
Also when the webcam is detected it is supposed to light up around the lens.
This has yet to happen when connected on Ubuntu.

Help? :]

---

### Post by ScottyPDX on 2008-10-02
I have the same webcam and have tried every driver there is (so far) and it won't play. HP won't support open source drivers, so hopefully there will be a driver in the next release (Intrepid). Otherwise, I filed a bug report for this one at [https://bugs.launchpad.net/bugs/276949](https://bugs.launchpad.net/bugs/276949) if you want to add anything to it.

Sorry.

---

