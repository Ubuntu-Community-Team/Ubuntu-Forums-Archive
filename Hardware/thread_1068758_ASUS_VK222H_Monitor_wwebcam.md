---
title: "ASUS VK222H Monitor w/webcam"
date: 2009-02-13
forum: Hardware
---

### Post by urbaneezer on 2009-02-13
I bought this new monitor and Ubuntu is not recognizing the webcam.

I've read about trouble-shooting audio and video issues on the Skype page but wanted to check here first to see if anyone knew anything about this particular monitor and issues.

I'm running 8.04 LTS.  

Thanks!

---

### Post by rkevinpreston on 2009-04-10
I just bought the same monitor...but I am running 8.10.  Anyone know how to enable it?  It's hooked via a USB cable from the monitor...and Linux knows it's there...I am wondering if there is a Windows driver workaround needed?

---

### Post by Sunfire523 on 2009-08-03
Hey, I am having the same problem, except with the new ASUS VK246H I just bought.  I suspect that they have the same webcam (1.3MP).  Ubuntu recognizes it, but when I open Cheese to take a picture, I simply get a lot of multi-colored lines and a bunch of static in the lower right corner.

Anyone have any ideas/workarounds?

I really appreciate the help!

I'm running Jaunty, 9.04

---

### Post by Sunfire523 on 2009-08-13
I have noticed that, while using Cheese (PhotoBooth replacement), the camera works for 3-4 mins, then gives out.  Anyone know how create a log file to log what is going on with this webcam?

---

### Post by IQRules on 2009-08-29
Can you post this?

$ lsusb

Mine is like this, I am thinking of buy 1 asus 24" with webcam.

untuHP:/tmp$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by windfix on 2010-03-01
I just ordered the Asus vk246h monitor, running 9.10 Karmic 64-bit.  Anyone found a solution for the webcam?  I'll post here if it works on arrival.

---

### Post by windfix on 2010-03-06
For anyone else considering - the webcam worked flawlessly with Karmic.  Instantly recognized in Cheese and Skype.  And it's a 1.3 Megapixel cam, much better than the 0.3 megapixel camera in my laptop.  SaWeeet!

---

### Post by athertek on 2010-03-16
Seems to work out of the box with 9.10
[http://www.ubuntuhcl.org/browse/product+asus-vk246h?id=7124]("http://www.ubuntuhcl.org/browse/product+asus-vk246h?id=7124")

---

### Post by urbaneezer on 2010-04-20
Bus 001 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 001 Device 003: ID 413c:2002 Dell Computer Corp. SK-8125 Keyboard
Bus 001 Device 002: ID 413c:1002 Dell Computer Corp. Keyboard Hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by c0nv1ct on 2010-10-10
ASUS VK246H's webcam not working here in 10.10.  Even after `modprobe uvcvideo` it is not listed in lsusb.

```
Bus 008 Device 003: ID 046d:c048 Logitech, Inc. 
Bus 008 Device 002: ID 1532:010b Razer USA, Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 131d:0156 Natural Point TrackIR 4 Pro Head Tracker
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

