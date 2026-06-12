---
title: "Intel graphics and xorg.conf"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by EisenPM on 2007-03-01
hello there,

does anybody of you know, if either one of these parameters work with an intel GMA 950 or other intel video card?

this is used for nvidia: 

Option          "RenderAccel"           "true"

this is used for ati:

Option          "backingstore"          "true"

it is supposed to help on these video cards to speed up 2D rendering on the desktop (e.g. drawing windows, etc.)

or maybe you know some allround or even intel specific tuning of the xorg.conf?

thanks!

---

### Post by pixeldotz on 2007-03-01
i have the same onboard video on my laptop. here's what i did to get 1280x800 and some tweaks working. it may or may not work for you.

enable the universe and multiverse repositories in the synaptic package manager.
then search for

915 or 915resolution

install
reboot

see how it works.

hope this helps.

---

### Post by EisenPM on 2007-03-01
thanks, but I don't need the resolution; what do you mean with some tweaks?

it's the tweaks I need, can't see anything besides resolution stuff in the man pages.

---

