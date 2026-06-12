---
title: "Problem with ATI Radeon XPress 1100"
date: 2008-05-01
forum: Hardware
---

### Post by Nesmontu on 2008-05-01
Hey,

I'm having a problem with 3D acceleration. I've tried installing the driver both from ubuntu's "hardware drivers" manager, and through envy-ng, but the result is the same.

Everything appears to be fine: glxinfo says direct rendering is enabled, fglrxinfo gives ATI and not mesa, fgl_glxgears works without a problem, and even the desktop effects work fine.
However, whenever I try to play a 3D game, it crashes with a segmentation fault :( This happens with games like chromium, sauerbraten, vegastrike, blobwars 2... And even some 2D games run slowly (eg blobwars 1)!

Any ideas what could cause this? Extra info I should give? Any help would be truly appreciated...

PS: the computer is a Dell Vostro 1000 laptop, in case that helps :)

---

### Post by Nesmontu on 2008-05-02
Sorry to bump, but I just realised something. Since compiz and (fgl_)glxgears are running fine, but the games are not, could it possibly be an sdl problem? If so, how do I find out?

Anyone with good ideas?

---

### Post by Nesmontu on 2008-05-04
Anyone?

---

### Post by BatKoos on 2008-05-09
Hi, I'm also having hassles with my ASUS laptop, running ATI Radeon Xpress 1100, if I install the ATI drivers any way I try...envyNG etc...I cannot reboot my laptop, when I do, I end up with a black screen...doesn't get to login to Ubuntu
I have to fix Xserver to get back in, but then the driver is disabled...managed to get it rebooting with the driver once or twice, but at some point I just end up fixing Xserver again...whatha...?
Please help, I'm a super-noob...!

---

### Post by txnec on 2008-06-13
i've also been having stability issues when the driver for my ATI xpress 1100 are used.  I get strange random errors saying that the system is unable to mount certain paths etc...  Eventually the system can't write to the drive.  When I repair xserver, the driver is disabled and my system remains extremely stable..  Anyone have any suggestions/fixes??

---

