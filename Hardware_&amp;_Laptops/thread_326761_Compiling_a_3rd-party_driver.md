---
title: "Compiling a 3rd-party driver"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by hartz on 2006-12-28
Hi there Kernel and driver Gurus

I am planning on compiling the driver for my webcam.  According to the notes in the documentation (here: [http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6)](http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6)), there are certain requirements for options which have to have been enabled in my kernel when it was compiled.  I probably have most if not all of those options on already in any case, but I will check it tonight and if and if neccesary recompile my kernel.

The document then goes on to say that I need to do "**make clean**" and "**make modules**".

My Question is: *Can someone explain what this does please?*  I recognize this from compiling the driver for my display card (nVidia).

I remember being surprised to find that after I compiled my nVidia driver, I did not need to reboot my computer - All I needed to do was restart X.  While this is all nice and wonderfull, it makes my wonder:  How does the kernel know that there is a new driver available which it can load, and what if I already had an older version of the driver on my system - how will the kernel know which version of two drivers with the same name to load?  Do I perhaps have to unload the driver if it is already loaded to get the new version to load?

Thanx for your help!
  _Hartz

---

### Post by hartz on 2006-12-28
Oh yes, I forgot to add:

For those interested, the driver I am about to compile is the Sonix driver for webcams with **sn9c10x** chipsets (available here: [http://www.linux-projects.org/modules/mydownloads/)](http://www.linux-projects.org/modules/mydownloads/)).  I see from my log files that, at present, version 1.27 of the driver loads when I plug the camera in, and I have downloaded the source which is for version 1.32, hopefully it will work better (My camera doesn't currently work, see my other thread here: [http://www.ubuntuforums.org/showthread.php?t=321862](http://www.ubuntuforums.org/showthread.php?t=321862))

---

### Post by weiersc on 2007-04-03
Hi,

Did you manage to get the camera working?

I just bought the same camera today and wonder if I should not try to return it.

---

