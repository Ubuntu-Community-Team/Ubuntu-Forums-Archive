---
title: "[SOLVED] Video Driver problems with 30-inch monitor in 7.10 (Gutsy)"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by GumbyX on 2008-03-10
I am running to a problem at work trying to get 30-inch Samsung LCD working on new Linux box they have me putting together. At the moment, it boots and shows the splash screen, but after that, it just sits at a black screen and does nothing. I can get to ttys, so the system is not hanging. 

Personally, I think the video drivers are causing the problem. The system has a nVidia Quadro FX 3500 dual DVI head PCI-E card. I have tired VESA, nv, and offical nVidia drivers (installed from the repositories) and nothing seems to work. The closed-source nVidia Drivers actually cause the system to hang. Does anyone have any ideas of why this might be happening or know of a way to fix this problem? I am totally out of ideas and need to get this system working soon.

Thanks ahead of time for the help.

PS I have manually configured xorg.conf with the proper sync and refresh rates, so I am pretty sure that is not the problem.

---

### Post by GumbyX on 2008-03-10
Dang it. My coworker just figured it out. Seems the drivers in nvidia-gxl-new won't work with the card, but the ones in nvidia-gxl do. : sighs: Something I didn't think about at all. Pleae ignore this. Mods, if you can delete this, I would appreciate it.

---

