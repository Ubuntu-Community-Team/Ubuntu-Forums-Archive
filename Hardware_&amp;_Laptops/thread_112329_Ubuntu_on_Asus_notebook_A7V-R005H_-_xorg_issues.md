---
title: "Ubuntu on Asus notebook A7V-R005H - xorg issues"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by SoundSquare on 2006-01-04
hello

I've been searching the web for quite some time before i decided to ask for help here. I just installed Ubuntu 5.10 on my Asus A7V R005H notebook a few days ago and i had several issues. My first issue with the onboard soundchip got fixed thanks to some infos i found on this forum and so i was able to complete the installation without the laptop freezing on the hotplug detection process (disabling the onboard soundchip in BIOS). Now I have an issue with display. When GDM starts i got a black screen, so the xserver seems to start but my screen remains black. I selected 1440x900 as the xserver resolution but also tried enabling only 1024x768 and smaller resolution with the same result. I also could not kill the xserver with CTRL/ALT/BCKSPACE as the server restarts automatically. I edited xorg.conf by booting on a Gentoo liveCD and everything seems ok (screenmodes, ati driver for the X700 etc..). I think something is wrong with the screen specs (horiz and vert frequencies) and i guess i got a black screen because the resolution is out of range. I'd like to enter manually the right frequency range into xorg.conf but i can't find these specs anywhere on the web.

got any idea ?

---

### Post by john_spiral on 2006-01-04
The below page might be useful:

[http://www.linux-on-laptops.com/asus.html](http://www.linux-on-laptops.com/asus.html)

---

### Post by SoundSquare on 2006-01-04
[QUOTE=john_spiral]The below page might be useful:

[http://www.linux-on-laptops.com/asus.html](http://www.linux-on-laptops.com/asus.html)[/QUOTE]

mine isn't listed but i'll have a look, thanks !

EDIT : nope, i couldn't find anything useful on this page.

---

