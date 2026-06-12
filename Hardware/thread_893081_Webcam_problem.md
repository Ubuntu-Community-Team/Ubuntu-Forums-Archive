---
title: "Webcam problem"
date: 2008-08-17
forum: Hardware
---

### Post by cgarib on 2008-08-17
Hi, my laptop comes with a webcam, and it doesn't work with linux. My laptop is a HP Pavilion dv6950. When i use lsusb command this is the output:
Bus 004 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 08ff:2580 AuthenTec, Inc. 
Bus 001 Device 001: ID 0000:0000 

Where can i get the drivers and how can i install them

---

### Post by spacedoggy on 2008-08-18
webcams and video input devices don't seem to have a simple install method in ubuntu, I can't even tell you the first steps in the right direction to install ANY webcam in ubuntu. I'd be intrested if you find a solution to this problem

SD.

---

### Post by luismanson on 2008-08-22
Your webcam is supported by the UVC driver, Linux version is here:
[http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices)
the module name you need to load is uvcvideo, try with the one included in the kernel, if that does not work maybe its an older version, you have to download and compile a new version from the website...

---

### Post by Mazin on 2008-08-22
Hopefully the help page at:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
may give you some tips.

---

