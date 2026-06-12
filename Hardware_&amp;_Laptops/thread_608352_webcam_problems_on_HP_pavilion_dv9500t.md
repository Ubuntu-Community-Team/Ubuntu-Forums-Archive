---
title: "webcam problems on HP pavilion dv9500t"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by JimmyBEng on 2007-11-09
I am trying to get the built-in webcam on my HP Pavilion dv9500t laptop.  lsusb identifies the webcam as the following:
```
 Bus 004 Device 002: ID 05ca:1812 Ricoh Co., Ltd
```

I have seen a number of references to a driver at [http://lsb.blogdns.net/r5u870](http://lsb.blogdns.net/r5u870), but that site no longer seems to exist.  There are several .deb files but they are all for 32-bit (and I am running 64-bit).  Long story short, I finally came across the source (will post link when I find it again).

I installed the r5u870 driver, but no applications seem to detect the camera.

I have noticed that some versions of the ricoh camera may use the uvc module as well, but I have had to blacklist the uvcvideo module to prevent it from loading during startup.   when this module is loaded is causes an error that kills modprobe and prints lots of info to dmesg including a stacktrace.  The side effect of this error was to stop usb from working.

I have not seen any references to the 1812 version of the camera anywhere else yet.

Has anyone else had any luck with this camera?  Any ideas on where I might find more info on getting this to work?

---

### Post by Whoopie on 2007-11-10
I found it here: [http://avilella.googlepages.com/r5u870-0.10.0.tgz](http://avilella.googlepages.com/r5u870-0.10.0.tgz)

Infos are at [http://avilella.googlepages.com/camera_notes](http://avilella.googlepages.com/camera_notes)

I don't have that laptop, so can't help.

---

### Post by scorp123 on 2007-11-10
> **JimmyBEng said:**
> I am trying to get the built-in webcam on my HP Pavilion dv9500t laptop.  lsusb identifies the webcam as the following:
```
 Bus 004 Device 002: ID 05ca:1812 Ricoh Co., Ltd
``` Are you sure that's the camera? On my dv2108ea all the "Rico Co. Ltd." devices are from the card reader and its sub-components, the camera is from "Microdia Inc." with a device ID of "0c45:62c0" ... And there are two different cameras makes in those HP laptops. For mine I'd have to use the "linux-uvc" driver and not the one you tried to use.

---

### Post by JimmyBEng on 2007-11-10
@ Whoopie
Thanks for the link.

@ scorp123
yes I'm preety sure that is the webcam.  Full lsusb output.
```
Bus 005 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 05ca:1812 Ricoh Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000
```

the smart card, etc. all appear under lspci for me.

I have been trying to use the uvcvideo module also, but it crashes modprobe on loading.  There is a whole stack trace in dmesg.  i attached the relevant part.

---

### Post by scorp123 on 2007-11-10
> **JimmyBEng said:**
>  the smart card, etc. all appear under lspci for me. Yes, you are right. My apologies. :)

---

### Post by JimmyBEng on 2007-11-14
So after loading the ricoh r5u870 driver module I see the following in dmesg
```
[ 2984.299875] Linux video capture interface: v2.00
[ 2984.337819] usbcam: registering driver r5u870 0.10.0
[ 2984.338025] usbcore: registered new interface driver r5u870
```

this seems hopeful but applications (skype and ekiga) still don't show anything.

---

### Post by gabrielitos on 2008-02-05
Hi!
I have the same problem with the same webcam, but my laptop is a HP Pavilion dv6560el.
I found the site mediati|wiki and I write an email to the developer asking to add my webcam among the supported ones, sending the files he needed to build the driver. In his svn is now avaiable a testing code with the support of our webcam, I have tried without success: I notice there is a simple bug in the Makefile; I can't test it because I've not the laptop now. Please check the driver (eventually with my Makefile corrected) and send the testing result to the developer!
Thanks
Gabriele

---

### Post by blumagic on 2008-03-31
All,

I have just recently purchased the dv9700t laptop. I have the same webcam and I am looking for a solution also. I hope that someone will resolve this issue. I have also had to blacklist the uvcvideo module. Hopefully once this module is fixed, we will be able to use the webcam. I will check this thread on a regular basis to hopefully someone will figure this out.

thanks,
blu.....

---

### Post by benvantende on 2008-05-05
Hey,

No image for me too on my HP dv9000. After a kernel headers update last weekend the blue light suddenly was active, meaning I have a /dev/video0 device I did not have before. Unfortunately no imagery though. Is it the uvcvideo module that needs to be fixed?

gRTz

ben

---

### Post by blumagic on 2008-05-06
All,

I have just upgraded from gutsy to the new Hardy distribution. Now I am able to unblacklist the uvcvideo module and still use lsusb and modprobe without my computer locking up.I still cant get Ekiga to show any video, but xawtv works in full screen mode only. So at least the webcam is working now. Now I cant get Ekiga to start up at all. So I have made two steps of progress with xawtv and one backward step with Ekiga. Anyway, I am closer and I hope this helps.

thanks,
blu.....

---

### Post by benvantende on 2008-05-06
it seems we have to wait until "05ca:1812" is supported on [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

it is not listed there.

gRTz

ben

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

