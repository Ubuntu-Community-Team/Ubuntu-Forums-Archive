---
title: "Ati Radeon X800 XL"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by Jun-Dai on 2005-04-28
Has anyone here successfully gotten Ubuntu/Gnome up and running with an Ati Radeon X800 XL?  It's the one card that Ati has that they don't seem to support yet (I posted a message about this in the Ati Divers thread in the Howto forum).  The trick is that I need X to run at 1280 x 1024 (it's the native resolution for my LCD), and it doesn't work right off the bat.  The xorg log spits out a list of Ati cards (it knows enough to know that I'm using an Ati card), and the X800 XL is the only one not in the list.  In the xorg.conf, however, if fills in all the appropriate information for the X800 XL.

I could probably run it in 1024 x 768, but I refuse to believe that to do stuff in my LCDs native resolution I have to stick to using Windows.

Also, what's Ati's usual turnaround time for putting out Linux drivers for their cards?  Would it be foolish to expect that they'll have one out this summer?  by the end of the year?  this decade?  Given that they have even the X850 XT in the driver package, it doesn't seem like it would be too long a wait, but maybe they're waiting to package it with their next line of cards (x900s?).

---

### Post by accuser on 2005-04-28
Which driver are you using? Check the "Device" section in your /etc/X11/xorg.conf file.

---

### Post by Jun-Dai on 2005-04-28
driver is "ati" and the device is correctly (to the best of my knowledge) identified as "ATI Technologies, Inc. Radeon X800 XL (R430 UM)"

xorg.conf and Xorg.0.log are here:
[http://chaumurky.net/~jundai/xorg/](http://chaumurky.net/~jundai/xorg/)

---

