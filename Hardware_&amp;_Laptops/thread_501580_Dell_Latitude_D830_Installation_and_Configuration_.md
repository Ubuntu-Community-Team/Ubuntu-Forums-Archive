---
title: "Dell Latitude D830 Installation and Configuration Problems"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by jb1789 on 2007-07-15
Hello,

I have been using Ubuntu on a 4 year old Dell Inspiron 8600 for about 3 months with absolutely no problems.  The installation went very well and all of my hardware was detected perfectly.

Since I had no problems installing, configuring, and using Ubuntu on my old laptop, I figured that I would have no problems installing it on my new Dell Latitude D830, but I was sorely mistaken.  I used the Alternate CD to install a barely functional system, then I booted into safe/recovery mode and ran sudo dpkg-reconfigure xserver-xorg to change the video driver from nv (NVidia Quadro 140M) to the generic VESA driver.  While I can now boot into Ubuntu and use the GUI, the display leaves a lot to be desired (i.e. the screensavers barely run; a moving window looks very funny...).  Additionally, neither the wired nor the wireless (Intel Pro/Wireless 4965 abgn) connections are functional.  I know that my wireless card will need to be properly configured, but Ubuntu does not even recognize it correctly.  Finally, the keyboard, but not the touchpad, stopped functioning twice, but worked again after a restart.

If anyone knows how to fix any of these problems, I would really appreciate the help because I am definitely not a fan of Vista.

Thanks in advance,

JB

---

### Post by vwaj on 2007-07-15
I'm in almost exactly the same position.  Unfortunately I don't have any answers right now, but if I find anything I'll let you know.  I have the same computer, same video card, and I just installed Ubuntu.  I installed using the Alternate CD and managed to get into the GUI using the VESA drivers.  My wired internet is working, but I haven't tried the wireless yet.  I have the same wireless card.

Right now I am working on finding a way to install the NVIDIA proprietary drivers; after I do that I'll actually be able to go to the screen's native resolution.  However, the install appears to be a little tricky.

Anyway, if you figure anything out, do post it -- I'm interested.

---

### Post by jb1789 on 2007-07-15
I downloaded the latest NVidia driver and tried to install it using NVidia's directions but I could not stop the X Server to install it without receiving numerous errors.  On the other hand, when I initially changed to the VESA driver, I manually set the correct resolution, so the WSXGA+ display looks nice, but any moving graphics are very glitchy, hence the need to install the proper drivers.

Even though Ubuntu does have many problems on this computer, it does run faster than Vista, so that is a plus. :)

JB

---

### Post by vwaj on 2007-07-15
Hi JB,

I managed to get the NVIDIA drivers installed.  I used a little tool called Edgy (available at [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) that did all the work for me.

Basically, I followed Flopy's instructions from [http://ubuntuforums.org/showthread.php?t=497049](http://ubuntuforums.org/showthread.php?t=497049).  Good luck!

---

### Post by jb1789 on 2007-07-16
When I try to install Envy using gdebi I receive the following error: Dependency is not satisfiable: xserver-xorg-dev.

Also, I tried manually installing the driver again, but the NVIDIA installer would not work unless I switched to "telinit 3".  Upon doing so, the x server started and brought up the GUI, which is unsuitable for installing the driver.

Any ideas?

---

### Post by vwaj on 2007-07-16
hmm...do you have all the repositories enabled?  perhaps it cannot find xserver-xorg-dev.

if that's not the problem then i'm not sure.  anyone else have any ideas?

---

