---
title: "22&quot; LCD 1680*1050 doesn't work"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by foerdi on 2008-02-02
HannsG 216DP Display

highest resolution doesn't work, there's a black big field on the left...

[http://ftp.utcluj.ro/pub/docs/how-to/mini-how-to/Modeline](http://ftp.utcluj.ro/pub/docs/how-to/mini-how-to/Modeline) says i should change modelines (HPE HPS bla bla)

xorg.conf before:
[http://ubuntuusers.de/paste/33023/](http://ubuntuusers.de/paste/33023/)

first i did was sudo dpkg-reconfigure -phigh xserver-xorg

xorg.conf after:
[http://ubuntuusers.de/paste/33137/](http://ubuntuusers.de/paste/33137/)

the DPMS option doesn't seem to help.

There's no problem with changing the resolution, it does NOT jump back to 1280*1024 or something similar, like i've read in other threads

my problem is still the left side.. black 10cm distance

please help me

thanks

---

### Post by rje_nc on 2008-02-02
Do you have an nVidia graphics card in your PC?  I have a similar issue with several different PC's on my monitor when I use the default nv driver.  On each system, when I install the nvidia proprietary driver the screen centers correctly.

Bob

---

### Post by foerdi on 2008-02-02
ATI Radeon 9200 PRO

---

