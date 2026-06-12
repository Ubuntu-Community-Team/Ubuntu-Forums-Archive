---
title: "nvidia and lg monitor"
date: 2008-08-12
forum: Hardware
---

### Post by blinX88 on 2008-08-12
so i have just installed Ubuntu 8.04 on my laptop. after some days of work i finally got my broadcom-card to work and everything else seems to be working fine. i also have an lg monitor for my PC and it works well with Ubuntu. i have done all the settings in "NVIDIA X server settings". the problem is that i can't get it to what i want at startup, i have to do the changes manually after. the first problem i had was that the application was not able to write to the X Configuration file, and the laptop screen was always the primary and only working screen when i first started up. i solved this with running the nvidia-setting as gksudo. so then i managed to get my monitor to always be the priamry screen. but then i ran into another problem, always when i booted up the screen resolution was changed to 1200x800 whenever i logged in. i want it to be 1680x1050. i have saved changes to the X configuration file, but it doesn't help. what can i do to get my screen resolution to be at 1680x1050 on startup?

---

### Post by blinX88 on 2008-08-13
bump..

edit: solved. i just had to change the settings in "screen resolution.

---

