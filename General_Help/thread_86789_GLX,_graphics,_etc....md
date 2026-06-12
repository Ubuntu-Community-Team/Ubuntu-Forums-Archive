---
title: "GLX, graphics, etc..."
date: 2005-11-06
forum: General Help
---

### Post by kverde on 2005-11-06
I'm new to desktop Linux, so forgive the basic questions, but...

I was trying to run tuxkart and scorched3d and something called glxgears and all complain that I do not have the glx module loaded.  My xorg.conf has it listed to be loaded.  Is it possible my graphics card is not supported?  It is on a Dell Laptop (700m) and seems to be using the i810 driver.  Does that mean I can not use 3d accelerated programs?  I've tried other people's xorg.conf to no avail.

Can someone hip me to the possibilities for me on this laptop?

Thanks for the help.

(ps. Ubuntu is really slick!)

---

### Post by Arktis on 2005-11-06
I don't know whether your graphics chipset is nvidia or ati (probably ati) but you need to follow one of the howtos on getting 3d accelerated drivers installed and then enabled in your xorg.conf.  They aren't installed by default because they are proprietary.  You can get them from the non free repos or you can manually install them after downloading.

---

