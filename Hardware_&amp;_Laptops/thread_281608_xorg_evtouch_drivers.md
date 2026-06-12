---
title: "xorg evtouch drivers"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by kev000 on 2006-10-21
hey all,

I'm trying to get my touchscreen working with edgy and It's just not taking. i've edited my xorg.conf to load the "evtouch" driver. I put the driver (evtouch.o and evtouch_drv.o) in /usr/X11R^/lib/modules/input but my Xorg.0.log tells me that "No Input driver matching evtouch". the kernel side of things work I believe because I can touch the screen and have the mouse move. However, the mouse moves everywhere but where my finger is . It would be awesome if anyone had any experience with this and could point me in the right direction. thanks

---

### Post by jge026 on 2006-11-04
Hmmm... you're getting farther than I did.  I had evtouch drivers working from source in the past (breezy & dapper), but I'm having trouble compiling in Edgy due to the new Xorg version.  Any tricks to compiling?

---

### Post by jge026 on 2006-11-04
One question... did you ever have this working, or did it just break due to dapper installation.  Its confusing to me that the X log would tell you that it can't find the driver, yet you still get the touchscreen to do **something**, even if its not what you wanted it to do.

Before, when I had it working, I configured the touchscreen (using ev_calibrate) to get the pointer to respond properly.  Have you done this step?

---

### Post by thor918 on 2006-12-29
hi.I'm trying to get the touchscreen of a lifebook b2131 working in ubuntu drapper.
after following instructions from [http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#download](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#download)
nothing works

I read this from xorg log
(EE) Failed to load module "evtouch" (loader failed, 7)

any ideas??


edit:
apparently my laptop touchscreen should be supported from kernel
[http://www.linuxquestions.org/questions/showthread.php?t=481845&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=481845&referrerid=195877)

---

### Post by thor918 on 2007-01-06
finaly got it working now. but still there are something wrong!, the mouse are whacked.
I had to swap y axe. but I set that in the evtouch parameter.
perhaps it works betther if I do the swap in modprob conf file like this:
[http://www.mp3car.com/vbulletin/showthread.php?t=79902](http://www.mp3car.com/vbulletin/showthread.php?t=79902)

the error I had was eliminated by doing this command:
 apt-get install xserver-xorg-video-nv

---

