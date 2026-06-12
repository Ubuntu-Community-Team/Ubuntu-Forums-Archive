---
title: "Mouse driver problems with Ubuntu 6.06"
date: 2007-01-12
forum: Hardware &amp; Laptops
---

### Post by obc on 2007-01-12
Hi

I have 6.06 loaded on a Dell Latitude 600, all working well, but the mouse is giving a few problems....
Checked out my old HDD with RedHat 7.3, no mouse problems, So I am assuming it is the driver, my messages log says:

localhost kernel: [17179698.532000] psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1    repeated many times.

and it is filling up very fast ......
The problem is the same with an external mouse (PS/2) 

How do I reload the driver,(Where is it ????) or get it to redetect the ps2 mouse / touchpad ?

Ypur help is most appreciated ....   Roger (obc)

---

### Post by obc on 2007-01-15
Hi 

Mouse problems solved by disabling the Intel speed step driver........

See the excellent post by mjwood0 on 21st Oct 2005 or search for CPU Freq Problem

---

