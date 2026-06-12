---
title: "Problem with TabletPC Acer 1825ptz"
date: 2010-06-06
forum: Hardware
---

### Post by josec89 on 2010-06-06
Hi.

I've just bought a TabletPC: Acer 1825ptz. It has a multitouch screen but I can't use it in Ubuntu 10.4 and I don't know how to configure it. 

Can anyone help me? 
Thanks.

---

### Post by pnefyp on 2010-06-10
[COLOR=#000000]Hello, are a genral procedure to activate the Cando-panel here
[http://lii-enac.fr/en/projects/shareit/linux-howto.html](http://lii-enac.fr/en/projects/shareit/linux-howto.html)
I am not able to activate it anyway, I followed the procedure but returns a compilation error. If you can activate the touch screen please post a reply.
Hello and good work!
(excuse my bad English)[/COLOR]

---

### Post by arobase40 on 2010-07-08
If you want to activate the Cando touchscreen for the 1825ptz, there is different ways to do so...

If you use the Cando driver from Enac with the standard evdev driver, you will have multitouch but with calibration issues !!!
From 2.6.35-RC2 to the lastest RC4, the kernel source is pre-patch with the Cando driver, but you will have to use xf86-input-evdev-2.4.0+ to be able to use the touchscreen without calibration problem.
The drawback is that it works only in monotouch style and impossible to use sort of right click on the screen.

Everything is explained here : 

[http://ubuntuforums.org/showthread.php?t=1483973&page=2](http://ubuntuforums.org/showthread.php?t=1483973&page=2)

The lastest tuto with 2 bonus (hardware acceleration for playing h.264 video,and no need to compile anything) is here, but again, only monotouch :

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

I'm trying to get multitouch (or at least dual touch) too but with no avail at the moment : no calibration issue but only monotouch or multitouch and calibration problem... ^^ :icon_frown:

---

### Post by modemlamer on 2010-09-09
does anybody get multitouching working?

actually 
single touch works but rightclick doesn't :(

even evtouch references from 
[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)


 "ONEANDAHALFTAP" doesn't work

---

### Post by arobase40 on 2010-09-11
> **modemlamer said:**
> does anybody get multitouching working?


Nope. Still on investigation.

> **modemlamer said:**
> actually 
single touch works but rightclick doesn't :(

even evtouch references from 
[http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)


 "ONEANDAHALFTAP" doesn't work

I don't know which version of xf86-input-evdev you use, but right click is disabled by default anyway since at least version 2.4...

You can try to watch at the source code and try to re compile...

---

