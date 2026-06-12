---
title: "Intel Video"
date: 2007-10-27
forum: Hardware &amp; Laptops
---

### Post by [z]ephyr on 2007-10-27
I've got a Dell 1420 with an Intel x3100 graphics chip, and I just installed the xserver-xorg-video-intel package and changed to the "intel" driver in my xorg.conf file (which really sped up compiz-fusion).  However, everything just has a general blurriness to it now that it didn't have before.  I'm not sure what the problem is - any ideas?

thanks,
[z]ephyr

---

### Post by SteFaNweI on 2007-10-27
do you use the right resolution - meaning the one your display works best?
use "sudo dpkg-reconfigure xserver-xorg" to choose a better one.

good luck ;)

---

