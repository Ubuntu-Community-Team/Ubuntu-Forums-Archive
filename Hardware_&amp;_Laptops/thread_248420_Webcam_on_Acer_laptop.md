---
title: "Webcam on Acer laptop"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by ephioz on 2006-09-01
I've been running Ubuntu on my Acer Travelmate 2441 for a while now, and everything works fine. The only thing that won't work is the integrated Acer orbicam webcam. What should I do to get it to work?:confused:

---

### Post by jjlido on 2006-09-13
hi, I have the same problem with an acer travelmate 4220, I cannot let the orbicam works.
Anybody can help?
<many thanks

---

### Post by Belyel on 2006-09-13
I have the same problem with mine (see [linky]("http://www.ubuntuforums.org/showthread.php?t=243787&highlight=travelmate+8200")).  There are lots of threads here that help with logitech quickcams (which are what acer uses in their computers).  Also, check out [spca5xx ]("http://mxhaard.free.fr/spca5xx.html")website to see if your cam is supported by that driver.  Search for spca5xx here for help installing.

---

### Post by whirl on 2007-05-27
Im trying to make my girlfriend make the switch to ubuntu but the biggest issues for her are the webcam and openoffice.. She has this TravelMate 2441WXMi and I was wondering if the webcam works nowadays with feisty?

Cheers o/

---

### Post by joe.turion64x2 on 2007-05-27
I have an Acer Aspire 5102WLMI laptop and have the same problem with the web cam. In my case it is because the drivers for the device (manufactured by Acer Labs Inc. according to Windows) have not been released (or even some technicals details). That is the same problem I have with the integrated SD card reader. I solved this last problem by getting an external USB card reader, and will be waiting until Acer ("out of the kindness of its heart") releases some driver/specs or some computer genius builds the drivers.
Anyway I prefer my digital camera (it has MUCH better resolution), and I am not a fan of video conferencing.

Thanks.
Joe.

---

### Post by Limon47 on 2007-06-04
Mine is Aspire 5051ANWXMi, same problem with the webcam. When I run Hardinfo, under the USB devices it gives the following device information: Product: USB20 camera; vendor: 0xc45; Product ID: 0x6260.
I have tried spca5xx so far no luck. I am very new to linux so any guide to make it works would be much appreciated. Thank you.

---

### Post by whirl on 2007-06-17
*bump*
Help, guides or advices anyone?

---

### Post by silverglade00 on 2007-06-18
Try it in ekiga. The problem might be the same one I have where Video4Linux 2.0 runs the camera just fine, but ekiga is the only app that supports version 2.0. Most everything else is still using V4L 1.0 only.

---

### Post by whirl on 2007-06-26
Cheers for the help but Ekiga doesnt find any video devices.

Anything else?

---

### Post by whirl on 2007-07-03
hate to do this but time to bring this up as we still need help with this :(

my gfs laptop acer travelmate 2441 WXMi has this "acer orbicam" or something and it isnt working. this is what it gives me when I type lsusb

uplim@comp:~$ lsusb
Bus 003 Device 003: ID 0402:5602 ALi Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c019 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

If I understood correctly its not supported right? Is there anything I can do?

Cheers for the help o/

---

### Post by joe.turion64x2 on 2007-07-03
> **whirl said:**
> hate to do this but time to bring this up as we still need help with this :(

my gfs laptop acer travelmate 2441 WXMi has this "acer orbicam" or something and it isnt working. this is what it gives me when I type lsusb

uplim@comp:~$ lsusb
Bus 003 Device 003: ID 0402:5602 ALi Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c019 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

If I understood correctly its not supported right? Is there anything I can do?

Cheers for the help o/
Unless the drivers are ready (there is a project in sourceforge) I am afraid nothing can be done. I am trying to make it work inside a virtual machine using Virtual Box, but again that would use Windows (it would be easier & faster to boot Windows instead).

Joe.

---

### Post by ephioz on 2007-07-10
Well it seems like there is little progress with the sourceforge driver, but one can always hope they'll finish it some day.. If you do get it to work in Virtual Box then please post here, not all of us have windows.. ;)

---

### Post by joe.turion64x2 on 2007-07-10
> **ephioz said:**
> Well it seems like there is little progress with the sourceforge driver, but one can always hope they'll finish it some day.. If you do get it to work in Virtual Box then please post here, not all of us have windows.. ;)
I haven't checked the sourceforge project for a while, but I hope they finish the driver at least before I replace the machine. I have not being successful until now to make the camera work in VirtualBox. The camera is recognized, drivers are in place, even the little green light starts blinking but at the end a Windows message tells me there is a problem with video memory. I will play with VirtualBox memory controls because perhaps I have assigned the machine very little RAM or video RAM.

Thanks.
Joe.

---

