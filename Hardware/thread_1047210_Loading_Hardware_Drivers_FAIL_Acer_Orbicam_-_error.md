---
title: "Loading Hardware Drivers FAIL: Acer Orbicam - error vc032x on boot"
date: 2009-01-22
forum: Hardware
---

### Post by zuperman on 2009-01-22
Hi, i'm an italian user, so sorry for my english.

I've an Acer Aspire 5630 with Ubuntu 8.10 (latest release).
At the boot it wait for 3 minutes (193 seconds) at the step LOADING HARDWARE DRIVERS. So i've removed "quiet splash" from menu.lst and i've seen this type of error (replicated many times):

14.896425] vc032x: check sensor header 44
[ 14.898544] vc032x: I2c Bus Busy Wait 0
[ 14.900546] vc032x: I2c Bus Busy Wait 0
[ 14.902545] vc032x: I2c Bus Busy Wait 0
[ 14.908672] vc032x: I2c Bus Busy Wait 0
[ 14.910694] vc032x: I2c Bus Busy Wait 0
[ 14.912686] vc032x: I2c Bus Busy Wait 0
[ 14.912691] vc032x: Unknown sensor...
[ 14.912710] vc032x: probe of 5-6:1.0 failed with error -22

On the web i've seen that is a problem of the driver of my integrated webcam... the module gspca.

I've tried to follow the step of configuration indicated on this site 
[http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/](http://paper0k.wordpress.com/2006/12/18/orbicam-finalmente-supportata/) 
but it didn't work (as many user say)

How can i do? I don't use the webcam... it doesn't matter... if i can't resolve it can i bypass this control or reduce the time?

Please help & thanks

---

### Post by zuperman on 2009-01-22
I've find this link... [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)
it works?

---

