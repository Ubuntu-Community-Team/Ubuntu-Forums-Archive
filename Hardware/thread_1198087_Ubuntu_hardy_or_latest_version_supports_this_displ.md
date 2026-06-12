---
title: "Ubuntu hardy or latest version supports this display card or not ?"
date: 2009-06-27
forum: Hardware
---

### Post by pumber on 2009-06-27
Gigabyte Radeon HD 4650 AGP Version

I would like to know if Ubuntu hardy or the latest version supports the above card or not.

By the way, I am going to upgrade the display card ?

What should I do in order to let ubuntu runs  perfectly ?(other than unplug the old card and replace it with the new one)

---

### Post by randomtask1 on 2009-06-27
Apparently it does not work properly. I have both ubuntu 9.04 and fedora 11 and neither one seems to work with this card. it seems to work fine until  you try to change the resolution and then all the colors go crazy.

---

### Post by pumber on 2009-06-27
So, which is the resolution you want to change to ?

Does it support it in WinXP ?

---

### Post by cariboo on 2009-06-27
You can use the opensource radeon driver for the video card. ATI hasn't seen fit to update drivers for older hardware. 

You will have to use older drivers in XP also.

---

### Post by randomtask1 on 2009-06-29
how do you change the driver for this card in Ubuntu?

---

### Post by Shake&amp;Fry on 2009-07-13
The card works in that you get good resolution out of it but...

With Jaunty, cannot enable desktop effects.  Cannot enable 3D acceleration.  Fglrx drivers do not detect any supported ATI Cards and neither do the ATI Catalyst drivers 9.6

So I tried installing Intrepid, same results.  I upgrade from an old ATI 9600 which lost 3D support with Jaunty, but even that would at least let me use desktop effects...

I'd suggest getting a NVidia card, I've seen 7300s with AGP interface, but they're more expensive.

---

