---
title: "Need help with ATI Radeon 9200SE drivers"
date: 2009-03-08
forum: Hardware
---

### Post by nickbadal on 2009-03-08
Hi, I'm trying to help a friend get his new graphics card working with his ubuntu system, which has an ATI Radeon 9200SE card. I tried installing the Xorg driver from the ubuntu repository, but after I restarted, it was all corrupted and wouldn't load the login screen and showed 2 color-corrupted loading screens frozen. 

     All of the tutorials I've found are for feisty and seem out of date. Can anybody help me out here?

---

### Post by ajgreeny on 2009-03-08
I have the same graphics card and it works wonderfully with the open source ati/radeon driver given it at installation time.  3d, compiz, etc etc, all work well, so I would uninstall the xorg-driver-fglrx you installed and then restart in recovery mode and when you get to the menu that appears choose **xfix **(or something similar, I can't remember exactly).  Let it run through then restart again and with luck you will have a proper screen display again.  Any problems, come back again and ask.

---

### Post by nickbadal on 2009-03-08
Ive gotten the graphics to work again by uninstalling the ati drivers and going back to the default ones. 
I would keep these drivers, but my friend wants to play World of Warcraft, and it runs about 3 fps with the standard drivers.

---

### Post by ajgreeny on 2009-03-08
OK, sorry I'm not a gamer so did not know that was so. I did try a long time ago to get the fglrx package to work with this card but gave up in the end when I realised I didn't need it for my computer use.

---

### Post by Neo_The_User on 2009-03-08
If you're going to use the open source drivers I recommend consulting this guide on compiling, building and installing libdrm and mesa from source as your graphics will be much faster than the versions in the repos.

[http://dri.freedesktop.org/wiki/Building#head-f566c8a09713eaa70d3ee69a3fd44fbc043f16cc](http://dri.freedesktop.org/wiki/Building#head-f566c8a09713eaa70d3ee69a3fd44fbc043f16cc)

Be sure to git clone dri2proto as well though.

git://git.freedesktop.org/git/xorg/proto/dri2proto

---

### Post by nickbadal on 2009-03-08
Okay, and after I do that, what should I do to make the new DRI work with WoW?

---

