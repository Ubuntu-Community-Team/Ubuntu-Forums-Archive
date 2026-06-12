---
title: "Poor 3d performance (nvidia, edgy)"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by HobbitG on 2006-12-08
I have a Geforce MX4000 128mb video card that i'm trying to use in Edgy.  However, i'm getting very poor performance.  I am testing using the first level on planetpenguin racer at 1024x768, on which i get about 10-15fps through the whole level.  Even glxgears looks really slow to me.

I have tried the nvidia-glx drivers, the nvidia-glx-legacy driver, and i even downloaded the drivers and installed from the nvidia site.  With each of these, i have confirmed loading glx support, so that's not the issue.

Is this card just not supported or am i missing something?

Full system specs:

Pentium 4 2.4ghz w/ hyperthreading
1 gig ddr400
Geforce MX4000 128mb
160gb sata150


Thanks in advance,
HobbitG

---

### Post by HobbitG on 2006-12-09
I just wanted to give an update.

It seems the poor performance is not because of some configuration problem, but the card is just alot slower than i remembered :P

But now i'm having another problem.  Installing all these drivers has broken something.  Whenever i reboot the machine, X fails to start saying that the kernel module is a different version than the X module.  I did an apt-get remove and reinstall on nvidia-glx and nvidia-glx-legace, with no success.  However, re-installing the driver package from the nvidia site works, but the problem reappears every boot, meaning i have to install every boot.  Does anyone have any suggestions for me?

Thanks

---

