---
title: "identifing  monitor"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by cdummy on 2009-06-16
There use to be a command
gksudo displayconfig-gtk
to identify monitor. This command is not working in 9.04.
Since 9.04 didn't detect my monitor highest resolution in pnp monitor is 800x600. Is there other way to change monitor type in 9.04 beside editing xorg. I'm hoping that if above command doesn't exist maybe there is even easier way. Thanks for help.

---

### Post by Mark Phelps on 2009-06-17
From what I remember, all that command did was bring up a window that allowed you to set resolutions based on display models.  That same function is now incorporated into 9.04 under Preferences --> Display (I think, I'm not at my 9.04 machine currently).

---

### Post by cdummy on 2009-06-20
This command allows You to choose monitor. If Ubuntu chooses pnp monitor for You than in preferences You only see 800x600 or below resolutions and there is no way to change this. I actually booted from Knoppix cd (recognises monitor no problem and gives 1024x768 fitting monitor) than i send to my gmail xorg.conf. After that cut and paste monitor section from xorg.conf to Ubuntu xorg.conf and I have proper resolution and proper monitor this is to complicated.

---

