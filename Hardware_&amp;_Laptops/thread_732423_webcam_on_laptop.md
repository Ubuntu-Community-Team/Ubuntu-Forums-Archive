---
title: "webcam on laptop"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by ve3dvv on 2008-03-22
Laptop: DELL Inspiron 1520

when I start camorama I got the message
Could not connect video device (/dev/video0). Please check connection


lsusb shows
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 

:- don't see anything I reconize in LSPCI

.
I guess there is no driver loaded??

At [http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html](http://www.debianadmin.com/how-to-configure-webcam-in-debian-linux.html)
they show 
05a9:2640  	OmniVision OV2640 (Dell Inspiron 1420/1720 notebooks)  	OmniVision

Any ideas to get the webcam working?

John, ve3dvv:confused:

---

### Post by linuxwizard on 2008-03-22
Alot of webcams will just work no need to add a driver. 
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by ve3dvv on 2008-03-23
BTW: running Ubuntu 7.10

Tried Ekiga and got an error message on config screen 8/10
Configpage 8/10
	Video input device
	Selected: Laptop integrated Webcam
	Testing: FAILED TO OPEN DEVICE

Any ideas that if driver is loaded or how to install one if it is not?:confused::confused:

---

### Post by ve3dvv on 2008-03-23
Thanks for the help!!:guitar::guitar


Got it working!!!

Note:
The Dell Inspiron 1520 uses the UVC-Linux Web Cam driver
This driver only supports V4L2. Currently you can use Ekiga and aMSN (SVN version)

In the Config page 
Config page 7/10
	Selected video Manager: V4L

Changed setting to: V4L2     and the camera works....:):)

BTW anyone got the camera working with Skype???

---

### Post by linuxwizard on 2008-03-23
Glad to hear you got your cam working. In my post I stated that you may have to work with the settings to get it to work. According to this > [https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) > your cam should work with Skype. It is listed under >  List of 'Fiddle to Get Working' Webcams.

---

### Post by Etrigan on 2008-03-31
Hello, i had a webcam integrated on my Dell Vostro 1400, 
follow your instruccions y can view my face whit Epiga jejeje.  (thank you!!!!)

whit lsusb on terminal  i see:
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.


then i installed the last UVS driver manually follow this tutorial [https://help.ubuntu.com/community/Webcam#head-1dfc8ed1ffc06f00ed45b0696fa0b27948954058](https://help.ubuntu.com/community/Webcam#head-1dfc8ed1ffc06f00ed45b0696fa0b27948954058)

but i cant use camorama .webcam visor.
can you help me? 

sorry my english.... is soooooo bad!! jejeje

---

### Post by linuxwizard on 2008-03-31
Camorama does not support v4l2.

---

