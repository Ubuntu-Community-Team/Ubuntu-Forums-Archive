---
title: "Microscope Camera Drivers"
date: 2008-12-22
forum: Hardware
---

### Post by oxman on 2008-12-22
I have a Micron MT9M001 chip microscope camera that I would like to run under ubuntu. Are there any drivers available for this? Any help is appreciated.

---

### Post by teaker1s on 2008-12-30
plug in turn on and terminal 
```
lsusb
```
post output and we can see your vendor and product id

---

### Post by oxman on 2008-12-31
Thank you for the reply.
```

Bus 007 Device 003: ID 0408:030c Quanta Computer, Inc. 
Bus 007 Device 002: ID 0100:0010  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```

It doesn't appear to even be mounting. Here is what I have on the camera:

The unit: Micron [YJEYE01-130]("http://www.made-in-china.com/showroom/nysrate/product-detailBMXJbequAPVY/China-USB-Digital-Eyepiece-YJEYE01-130-.html") with an MT9M001 chip. 

The source: [Light Livestock Equipment-Camera]("http://www.lightlivestockequipment.com/Manuals/MicroscopeCameraInstallation%20instructions.pdf")

The chip specs: [Here]("http://download.micron.com/pdf/datasheets/imaging/mt9m001_1300_mono.pdf") or [here.]("http://www.tavcso.hu/egyeb/mikroszkop/td-130.pdf")

I tried gspca module loading to no avail.

---

### Post by teaker1s on 2008-12-31
googling it appears that this camera uses video4linux and mentions needing a patch. 
Have you tried latest video4linux in repositories?

it also appears to be kernel related,while I don't know the answer these should help

patch reference here
[http://lists.zerezo.com/video4linux/msg21274.html]("http://lists.zerezo.com/video4linux/msg21274.html")

[http://www.linuxhq.com/kernel/v2.6/25-git10/drivers/media/video/mt9m001.c]("http://www.linuxhq.com/kernel/v2.6/25-git10/drivers/media/video/mt9m001.c")

lastly video4linux wiki has various articles and irc for live chat
[http://www.linuxtv.org/v4lwiki/index.php/Main_Page]("http://www.linuxtv.org/v4lwiki/index.php/Main_Page")

---

### Post by oxman on 2008-12-31
> **teaker1s said:**
> googling it appears that this camera uses video4linux and mentions needing a patch. 
Have you tried latest video4linux in repositories?

it also appears to be kernel related,while I don't know the answer these should help

patch reference here
[http://lists.zerezo.com/video4linux/msg21274.html](http://lists.zerezo.com/video4linux/msg21274.html)

[http://www.linuxhq.com/kernel/v2.6/25-git10/drivers/media/video/mt9m001.c](http://www.linuxhq.com/kernel/v2.6/25-git10/drivers/media/video/mt9m001.c)

lastly video4linux wiki has various articles and irc for live chat
[http://www.linuxtv.org/v4lwiki/index.php/Main_Page](http://www.linuxtv.org/v4lwiki/index.php/Main_Page)

Thank you for the great leads and your time and effort. I'll have to do some homework to learn how to install a patch. This is the same track I was on and I appreciate the conformation.

---

