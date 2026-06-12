---
title: "Upgrade to 9.10 failed."
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by honeybear277 on 2009-11-11
I've managed to completely screw up my Ubuntu 9.10 installation. I have been running 9.04 for some time and everything was fine. I then upgraded to 9.10 today using the updater and it worked ok except that my wireless network (Atheros ar2413) no longer worked. So I shutdown my computer and pulled it out and restarted it. No problem. I then reinstalled the card and that is where it all went pair-shaped.

On boot-up x windows does not start. Instead I get the error message: "Mount of filesystem failed. A maintenance shell will now be started". In this text window I can log in, navigate around the filesystem and everything is there. I tried a startx but it was unsuccessful. I get "Read-only file system" type errors.

Does anyone know how I can repair this?

---

### Post by jeb800e on 2009-11-11
Probably just a glitch, as Karmic is new. Why don't you try doing a fresh install of 9.04 and wait a few weeks to update back to 9.10, if you choose.

---

### Post by matpol on 2009-11-11
Have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1306345](http://ubuntuforums.org/showthread.php?t=1306345)

I had similar problems and this sorted it out.

---

### Post by honeybear277 on 2009-11-11
Thanks guys. I am trying the other thread you mentioned and if that doesn't fix it I will reinstall 9.04.

---

### Post by honeybear277 on 2009-11-11
OK, I got it working. I did a "fschk /dev/sda1" and this found a couple of broken chains and fixed them. Ubuntu boots up correctly now.

Now to get my wireless network card working....

---

