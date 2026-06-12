---
title: "Packard Bell PB-WC100 Webcam in ubuntu"
date: 2008-07-16
forum: Hardware
---

### Post by adrian007 on 2008-07-16
Hello all. i have a Packard Bell PB-WC100 Webcam and i am wondering if it works in linux/ubuntu as i can not make it work and have not found drivers anywhere on the internet. the web cam has not been detected by any software i try 

Thanks For Any Help:):):):):):):):)

P.S if it is any help here is the output of lsusb:

> Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 043d:00b2 Lexmark International, Inc. 
Bus 001 Device 004: ID 05a9:a518 OmniVision Technologies, Inc. 
Bus 001 Device 003: ID 07d1:3c03 D-Link System 
Bus 001 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000 

---

### Post by jmmL on 2008-09-09
I hope you're still checking this post!

If you haven't already fixed it, it would appear that your webcam is supported by USB Video Class (UVC). Here is the link: [http://linux-uvc.berlios.de/]("http://linux-uvc.berlios.de/"). Search for "05a9" on the page, as I'm 99% sure that your webcam is the "OmniVision" device.

Unfortunately I know nothing else about UVC, and I don't (yet) have a laptop with integrated webcam. Hopefully the link is enough to get you started!

---

