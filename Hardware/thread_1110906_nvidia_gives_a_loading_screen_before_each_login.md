---
title: "nvidia gives a loading screen before each login?"
date: 2009-03-30
forum: Hardware
---

### Post by What_the_deuce on 2009-03-30
I upgraded to the nVidia 180 drivers through Synaptic, and now before each login I am given a black screen with the nVidia logo and 'beta driver' in big red letters. 

Is there a way to get rid of this screen?

Thanks!

---

### Post by nlz on 2009-03-30
I had this too when I installed the NVDIDIA drivers with the official installer.
Look in /etc/X11/xorg.conf and you can find it, try uncommenting a line by putting a # in front of the line and restart the X-server (by typing sudo /etc/init.d/gdm restart) and see if you see the screen coming by.

---

### Post by simtaalo on 2009-03-30
[http://ubuntuforums.org/showthread.php?t=994829](http://ubuntuforums.org/showthread.php?t=994829)

---

