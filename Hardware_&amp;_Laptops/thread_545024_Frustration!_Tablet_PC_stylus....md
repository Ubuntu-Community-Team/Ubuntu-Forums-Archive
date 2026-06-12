---
title: "Frustration! Tablet PC stylus..."
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by frith on 2007-09-07
Okay, so I have been searching for a solution for this one all day it seems...

I'm running Fiesty on a toshiba m200 (its a tablet pc which won't boot from anything and it was a mission to install it on there let me tell you..) and at first the stylus worked fine. Now it doesn't.

I have made a few changes, but I have changed everything back (i used the sudo dpkg-reconfigure -phigh xserver-xorg command, and the similar one for gdm). I also uninstalled (with apt-get remove and dpkg -P) all the modules relating to anything to do with wacom and reinstalled them after rebooting.

I found the following page:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/66646)

and after doing basically the same thing as this person, I get the same results. That is, it seems like the tablet is detected but not operational. I'm not convinced this is a bug because it did work when I first installed (in August). It might have been smashed in the recent update, I couldn't say for sure.

Anyone got any advice? I'm tearing my hair out...

Frith

---

