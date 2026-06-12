---
title: "ubunto works but i cant make anything out"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by kelvinl on 2006-01-11
Hi i installed ubuntu onto my computer.  I partitioned my drive so that i can run windows.  The problem lies when i run ubuntu.  When i do i can hear it running and the introductory sounds.  But the image that appears is a whole bunch of squares, well small squares say like 1/4" in length and about 1/8" in width.  I dont have onboard video, I use a nvidia e-geforce 6600, i was thinking maybe the nvidia drivers arent installed for linux? but when i look at the guides it seems like i need to be able to have a ubuntu graphics in order for me to install them.  Well i would appreciate any help, i'm really new to linux, so if this is a stupid questions please forgive me.  :p

---

### Post by kaamos on 2006-01-11
Press ctrl+alt+F1 and login. Use the command```
sudo dpkg-reconfigure xserver-xorg
```
Try selecting the "vesa" driver. Or use nv and try different options..

Hope this helps!

---

### Post by kelvinl on 2006-01-11
thanks for your help.  Its not working but... It got me a little closer to the solution :D

---

### Post by jerrykenny on 2006-01-11
Kelvin , that corruption may be due to your xserver demanding some crazy refresh rate from your Monitor.

If that 's the cause dont run with it for any long period, it might damage your monitor


Edit your xorg.conf

from the comman line (rescue mode) type   nano /etc/X11/xorg.conf

goto the section about Monitor, check the Vertical synch range, a very high refresh rate may be enabled here, try limiting the upper figure to 80, then startx

---

### Post by kelvinl on 2006-01-11
I used the sudo's to update my nvidia driver.  Its working now!!.  Anyways thank you guys for your help.  Cause I didnt even know how to get into the kernel, or w/e its called to get to the point where i can enter sudo commands

---

