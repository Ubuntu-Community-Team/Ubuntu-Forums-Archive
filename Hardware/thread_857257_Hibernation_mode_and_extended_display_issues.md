---
title: "Hibernation mode and extended display issues"
date: 2008-07-12
forum: Hardware
---

### Post by leomedia on 2008-07-12
Hi all,

I have a newly ubuntu 8.04 distro installed in dual boot (vista) on my Toshiba Satellite M200 (i965 chipset). Everything's fine except 2 things :
- I can't use the 'hibernate' state because the laptop actually shuts down but has trouble to mount its partitions when I reboot
- I've got a 1280x1024 external LCD plugged on my vga port but I can't use any 'extended desktop' display mode (my laptop native resolution is 1280x800) but only the clone one, whether or not the clone box is ticked. It works under vista, any clue to do the same with Ubuntu ?

BTW Ubuntu 8.04 distro (and support) is the really first linux one which made me decide not to go with windows any longer.

leo

---

### Post by ProbablyX on 2008-07-12
Hi,

What power manager are you using? AFAIK powertop and kpowersave handle stuff differently, KPowerSave works fine for me on my MacBook and powertop works better for my mate with a Lenovo laptop. You can try switching powertop / kpowersave and see if there is any difference. Just shut off powertop (if youre using gnome) and start kpowersave (which is a kde app but will work under gnome - you might have to install it first)

---

