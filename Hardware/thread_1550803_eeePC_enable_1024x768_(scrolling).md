---
title: "eeePC enable 1024x768 (scrolling)"
date: 2010-08-11
forum: Hardware
---

### Post by Benjamin888 on 2010-08-11
How can I enable 1024x768 resolution on my eeepc 901 with scrolling. I know that you can do this with windows xp installed. I did a little bit of research and I believe I need to install i810 drivers and edit the xorg.conf file.

How would I do these steps exactly?

---

### Post by kerry_s on 2010-08-11
your most likely using the right driver already.

so you would just need to modify the /etc/X11/xorg.conf, but first you need to make a xorg.conf.

when booting hold the shift key to get the menu, select the recovery mode, select root shell. type "X -configure" that will make a xorg.conf which you can then copy to /etc/X11/xorg.conf.

thats as far as i know.

---

