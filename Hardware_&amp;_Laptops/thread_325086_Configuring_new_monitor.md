---
title: "Configuring new monitor"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by zergberg on 2006-12-25
I just pulled a "new" monitor out of my uncle's basement. I know it supports 75Hz refresh at my resolution, but I can't set it to that.

How do I fix xorg.conf (or whatever) so that I can?

---

### Post by mojoman on 2006-12-26
If you're going to use the new monitor for a while you'll probably want a xorg.conf generated for its specs. You cold try to connect it, start up the system, auto-generating a new xorg.conf in the terminal using:

sudo dpkg-reconfigure -phigh xserver-xorg

and then just rebooting the system. Make sure to have a back-up of your working xorg.conf if you're going to switch back to your old monitor or if something bad happens...

/Mojoman

---

