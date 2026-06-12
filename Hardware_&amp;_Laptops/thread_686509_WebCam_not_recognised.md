---
title: "WebCam not recognised"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Angadude on 2008-02-03
Hello,

I have an Intex Batman 350K WebCam. It doesn't have company provided Linux Drivers.

Here is my lsusb:

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05fe:2001 Chic Technology Corp. 
Bus 001 Device 001: ID 0000:0000  


I suppose this:
Z-Star Microelectronics Corp. ZC0303 WebCam

would be my webcam, and the other one my Wireless Keyboard's.

So I tried this:

camorama -d /dev/bus/usb/002/002

Gives me connection error.
 
I suppose I need a driver? Could anyone tell me where I could get one and how I could install it? I'm a Linux N00B.

PS> I tried to install Windows Driver with Wine, it installs, but camera isn't detected.

---

### Post by bwhite82 on 2008-02-03
See this post:

[http://ubuntuforums.org/showthread.php?t=686530](http://ubuntuforums.org/showthread.php?t=686530)

---

### Post by Angadude on 2008-02-03
tried that...building gives errors...

---

