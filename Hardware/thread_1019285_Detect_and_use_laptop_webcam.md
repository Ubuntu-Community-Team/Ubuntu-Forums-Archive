---
title: "Detect and use laptop webcam"
date: 2008-12-23
forum: Hardware
---

### Post by ajyrds on 2008-12-23
Hi,
I have a HP DV6500 and Hardy heron loaded on it. This might be a very stupid question but please let me know how I can detect my webcam and use it with application.
Is the webcam detected as a usb device? I tried lsusb and this is the output -
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

I also tried to detect it using Easycam, but it gives me the error 'No camera, no compatible camera found.'
GuvcView gives the error - "Unable to open device. Please make sure the camera is connected and that the linux-UVC driver is installed."

What should I try next? Can somebody please help?

Regards,
Ajay

---

### Post by teaker1s on 2008-12-30
[https://wiki.ubuntu.com/HP_dv6000_Series]("https://wiki.ubuntu.com/HP_dv6000_Series")

---

### Post by ajyrds on 2009-01-04
Thanks!
I already have tried it, meaning checked the output of 'lsusb'. It does not show my webcam - only one device is detected, with the hardware id 03f0:171d. This is for the bluetooth module.
Any idea what I should do when a device is not showing up in the output of lsusb?

---

