---
title: "Resolution Problems in Feisty"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by mcallenSchmee on 2007-06-05
The only way I can get my screen resolution to 1024x768 is if my monitor is unplugged when booting up or when restarting X. The rest of the time it just goes to 800x600. I've tried removing all other resolutions from the xorg.conf file but it still goes to 800x600. I've tried using both the "savage" and "vesa" drivers. I've also already tried:
```
sudo dpkg-reconfigure xserver-xorg
```

My motherboard is an "ECS Elitegroup L7VMM3" with integrated video, and my monitor is a "Compaq MV540". Resolution went up to 1024x768 in Dapper Drake, but X crashed if I tried to change it.

Does anyone know how I might make the resolution stay at 1024x768  without having to unplug it at every boot?

---

### Post by mcallenSchmee on 2007-06-07
I had also previously tried adding a modeline from an online generator into the xorg.conf file, but it didn't work. I looked in the Xorg.0.log and saw that it said something like "pixel clock out of range". I changed the pixel clock number in the modeline to something that was supported, and now it works.

---

