---
title: "No 3D Acceleration on IBM X61 (Xubuntu 7.10)"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Hazze2 on 2008-02-05
Hello!

I have installed now Xubuntu on my IBM X61s and I do not have 3D Acceleration. For glxinfo | grep rendering I get the answer direct rendering: No. Following drivers are installed: Intel -Experimental modesetting driver for l... and vesa - generic vesa-compliant video cards. 
How can I activate the 3D Acceleration? Because I would like to use the 3D desktop environment...

Thank You!

Regards
Hazze2

---

### Post by neurostu on 2008-02-05
Did you check out thinkwiki.org?  I found a ton of great information that helped me install Ubuntu on my T61.

Check out this [COLOR="Navy"][link www.thinkwiki.org]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_an_X61_Tablet#Graphics_Card")[/COLOR]

---

### Post by mbsullivan on 2008-02-07
Hi Hazze2,

Getting 3D acceleration on x61 used to be iffy, but Gutsy drivers should work fine.  Try installing xserver-xorg-video-intel (assuming that you're working off of Gutsy repos):

```
sudo aptitude install xserver-xorg-video-intel
```

The Gutsy version should provide stable 3D acceleration.  After it's installed and you restart X, make sure that the "Generic Video Card" section of /etc/X11/xorg.conf looks like:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
```

Let me know how this works! I'm one of the x61ers on the forums... and we should be able to get almost everything working for your laptop.

Mike

---

