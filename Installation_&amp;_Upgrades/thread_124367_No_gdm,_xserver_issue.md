---
title: "No gdm, xserver issue"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by Domhnull on 2006-02-01
I just did a clean install of Breezy on a new machine (fresh hard drive, everything).  The install seemed to go okay but instead of going to gdm I get a blank screen.  The system is working.  I can type CTRL+ALT+F1 and switched to a text-based login and get in just fine.  There aren't any errors listed in the bootup sequence.  But if I go to CTRL+ALT+F7 I'm back to the blank screen.

I've tried ```
sudo dpkg-reconfigure xserver-xorg
``` several times but so far  I haven't had any luck getting this to work.  The machine is a VIA EPIA M10000 with an integrated video chipset.  I tested it with a Damn Small Linux USB boot drive after putting the thing together and it load just fine, went right into the desktop just as it should.  I'm open to suggestions, just a bit surprised that it isn't working under Ubuntu.

---

### Post by arckeda on 2006-02-01
switch driver to vesga(might have spelled it worng)

---

### Post by Domhnull on 2006-02-01
Thanks for the suggestion.  I switched to the vesa driver and it worked fine.  The new system is up and running great.

---

