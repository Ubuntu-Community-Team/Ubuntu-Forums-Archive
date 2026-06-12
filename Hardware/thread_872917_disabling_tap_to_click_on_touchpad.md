---
title: "disabling tap to click on touchpad"
date: 2008-07-28
forum: Hardware
---

### Post by aaronLund on 2008-07-28
Big noob here, so I apologize.

Anyway, I've been scouring the internet trying to find a solution to a problem that's really been bugging me.  

I'd like to disable the "click" ability of my laptop's touchpad. According to System 76, it's a Pangolin Value panv3.  Sounds like there is plenty of info out there on how to disable the touchpad completely but, obviously, that would be throwing the baby out with the bath water.  I use it to mouse around, just don't need its "click" abilities.

I've tried all sorts of SHMConfiguration stuff to no avail.

Thanks.

-Aaron

---

### Post by Potatoj316 on 2008-07-28
you need to edit your xorg.conf file, post it here and I can tell you what to comment out (/etc/X11/xorg.conf)

```
cat /etc/X11/xorg.conf
``` in a terminal will show you the file

---

### Post by Tsarj on 2008-07-31
On Gutsy ubuntu, go to System on the panel > Preferences > Mouse and there's an option in there to "Tap to click" on the Touchpad tab.

---

