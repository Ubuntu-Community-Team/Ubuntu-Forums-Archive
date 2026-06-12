---
title: "Radeon hd 3400 proprietary driver issues"
date: 2010-02-11
forum: Hardware
---

### Post by Jammerton on 2010-02-11
I installed ubuntu 9.10 Karmic Koala on my girlfriends dell studio 1535 laptop.  Everything works great EXCEPT the graphics card.  The graphics card is a radeon hd3400.  I first went with the default open source driver which did not have 3d support.  I then used the proprietary driver via system/administration/hardware drivers.  The proprietary driver enabled 3d support, but after enabling compiz the graphics were glitchy.  All my refresh rate settings are at 60.  and  have anti aliasing enabled via the catylist control center.  STILL get tares. and glitches, however I did notice that it was less pronounced after turning on anti aliasing and setting all refresh rates to 60 (in compiz, catylist control center, and display).  I hope I'm missing something here.  If anyone has any info regarding this dilemma please let me know.  Im trying to one up her sisters mac book and prove that linux is king.  someone help!!!

---

### Post by hxcobd on 2010-02-11
After using the proprietary driver from Hardware Drivers, did you test out any benchmarking or 3D games to see how the performance is?

If you're getting good performance and framerates, it may simply be a matter of finding a newer driver where the "kinks" are worked out.

I'd scope out ATI's Support website; they have newer versions of proprietary drivers for linux on it.

---

### Post by Jammerton on 2010-02-11
ok. so I go to the ati site, and they say I need these packages. 

 XFree86-Mesa-libGL
libstdc++
libgcc
XFree86-libs
fontconfig
freetype
zlib
gcc

Ive only tried to get xfree86-mesa-libGL, but I cant find it anywhere.

---

### Post by markbuntu on 2010-02-12
The driver available with 9.10 is not the best for that card, which is a Mobility 3400 which is not quite the same as the IntegratedGraphicsProduct 3400. Your best bet would be to remove whatever proprietary driver you have installed now and then download the one from the ati site and make the installer executable and run it. Don't worry about those packages, you already have them.

---

