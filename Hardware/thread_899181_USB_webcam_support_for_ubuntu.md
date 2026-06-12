---
title: "USB webcam support for ubuntu?"
date: 2008-08-24
forum: Hardware
---

### Post by pankirk on 2008-08-24
I'm thinking about buying this product **HP USB Webcam, EW193AA** is the name of it, and heres a link to it on amazon: [http://www.amazon.com/HP-VGA-Webcam-EW193AA-ABA/dp/B000NWMEJA]("http://www.amazon.com/HP-VGA-Webcam-EW193AA-ABA/dp/B000NWMEJA")

I just want to know if it will work on ubuntu hardy heron 8.04. I would like it to work with these applications: cheese, adobe flash player (9 is the version i think) and probably some sort of chat application like pidgin(i dont think it supports video chat...). Anyway yeah thats it. Is there any way it will work, with or without setting up drivers? Or do you have a better product i should get? Thanks in advance!

---

### Post by libra1780 on 2008-08-24
as shown here
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras")
your cam is not in the wiki list. maybe it's a clone of one of them. would be good to know the chipset it uses...

---

### Post by pankirk on 2008-08-24
Hm. Well, I will try to find some sort of other camera from that list... ? It's hard to find these in normal stores...

---

### Post by Crafty Kisses on 2008-08-25
Go with Logitech they usually always work. (QuickCam)

---

### Post by IntuitiveNipple on 2008-08-25
I downloaded the Windows driver from HP and 'installed' it using Wine to get access to the driver's **Pa707ucm.inf** file. It shows the PCI ID of the camera is: **USB\VID_093A&PID_2608&MI_00** which is a Pixart PAC7311 chip-set.

Quite by chance I've been helping someone else who is [trying to get a Pixart-equipped camera to work](http://ubuntuforums.org/showthread.php?t=900250). In their case there is currently no Linux driver keyed to the camera's PCI ID, but the **gspca** driver supports many Pixart-based cameras and we're experimenting with enabling support for the camera in the gspca driver.

The good news for you is, I just happened to have the source-code of the gspca driver open when I was browsing and saw your question. After checking the Windows .inf file I can tell you that **the gspca driver supports the HP EW193AA camera**.

According to the [gspca camera compatibility table](http://mxhaard.free.fr/spca5xx.html), your camera is also known as the Trust WB 300P.

Hardy ships with gspca v1.00.18 but it is possible to update to v1.00.20 (from Intrepid) if necessary (see the [previously mentioned webcam driver experimentation](http://ubuntuforums.org/showthread.php?t=900250)).

---

### Post by pankirk on 2008-08-25
So what does this mean? I can get my camera working with Cheese, Skype, and other video protocol programs? Great is there a tutorial?

---

### Post by Crafty Kisses on 2008-08-25
Yeah.

Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

