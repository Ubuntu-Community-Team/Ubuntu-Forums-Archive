---
title: "Laptop Webcam How to Install Driver?"
date: 2008-10-07
forum: Hardware
---

### Post by robbie_tzr on 2008-10-07
I've been trying for some months now to get the webcam in my laptop to work in Ubuntu Hardy Heron - it's based on the Clevo 520N chassis with an integrated empia 2750 webcam. Basically, if I can get this to work then it's finally goodbye to Vista, as it's the only piece of hardware not recognized in the laptop.

I'd pretty much given up until google brought this up:

[http://cateee.net/lkddb/web-lkddb/VIDEO_EM28XX.html](http://cateee.net/lkddb/web-lkddb/VIDEO_EM28XX.html)

And there in the list is my device: eb1a 2750 !!!!

Please can someone explain how exactly I can use this to enable the webcam - the documentation is somewhat sparse, and what little there is does not make sense to me.

I would be really really grateful for any advice.

Thank you!

---

### Post by del_diablo on 2008-10-07
Is there a on/off key on it?
Attempted to update to the current beta? [Here](http://www.ubuntu.com/testing/intrepid/beta#Upgrading%20from%20Ubuntu%208.04) You get it up this way.
Maybe its included, i don't really know. Or you will have to compile a driver(someting i got no clue on).

---

### Post by beno1990 on 2008-10-07
A lot of webcam drivers are in the Hardy backports kernel modules package, which you can get by going to System -> Administration -> Software sources, and then go to the updates tab and check the "Unsupported updates (hardy-backports)" box and bring up Synaptic, click reload, and then search for something like "hardy backports". This should give you a list of packages, choose the version for the kernel you have installed.

These packages have the drivers for *most* laptop webcams and such, but not all.

---

