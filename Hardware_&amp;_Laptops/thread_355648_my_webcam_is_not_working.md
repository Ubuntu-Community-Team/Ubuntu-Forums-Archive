---
title: "my webcam is not working"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by zolly on 2007-02-07
I have a webcam GemBird CAM55U but it is not working with [http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070110.tar.gz)

Any solution ? Other drivers ?

---

### Post by Belyel on 2007-02-07
I'm going to assume that you used a tutorial here on the forums for installing that driver.  It's not very difficult, but if you mess it up, it obviously won't work. The first thing you should check before installing it again (ie retrying the same thing), is to see if it is even a valid driver for your camera.  In a terminal, type ```
lsusb
``` and see what comes up.  There should be a listing for something that looks like your camera.  For example, when I type it in, I get ```
Bus 005 Device 003: ID 046d:0892 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 
```  where the logitech line is obviously my camera.  The device id ****:**** is what you need to look for on the website where you found the driver.  He has a list of all the cameras for which the driver applies.  If your camera is not listed, it will not work.  Try a search here on the forums for your device ID (or part of it), and also try Google.  It's possible that someone else has a driver for it.

---

### Post by zolly on 2007-02-10
It is:

Bus 001 Device 005: ID 0ac8:307b Z-Star Microelectronics Corp.

---

### Post by zolly on 2008-04-27
see:
[http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/](http://quilombo.wordpress.com/2008/02/02/zaapa-webcam-en-ubuntu-linux-710-gutsy-gibbon-2/)

it has the same ID with my webcam.

Follow the instructions and it will work.
(It use the latest driver gspca)

To use Yahoo Messenger with webcam install:
kopete and libjasper-runtime

---

