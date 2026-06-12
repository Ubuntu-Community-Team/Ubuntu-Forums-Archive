---
title: "Can't get drivers for wireless card, graphics chip (HP Pavilion dv6000)"
date: 2010-01-30
forum: Hardware
---

### Post by dasThumbtack on 2010-01-30
Hey guys, I just installed Ubuntu today. It seems pretty nice, except I can't get proprietary drivers for my graphics chip and wireless card. When I booted from the live CD, the Hardware Drivers utility had a list of available proprietary drivers for this hardware. However, when booting from the hard drive that list is empty. By the way, here are what they were:

Broadcom B43 Wireless driver
NVIDIA accelerated graphics driver (version 173)
Broadcom STA wireless driver
NVIDIA accelerated graphics driver (version 96)
NVIDIA accelerated graphics driver (version 185) [Recommended]

Googling for these hasn't really helped, and if even if I found them I wouldn't know what to do with them. 
So yeah...Thanks :D

---

### Post by halj32 on 2010-01-30
you will find the drivers for your wifi on the CD, or if your on line run in a bash shell
 sudo apt-get update
then
sudo apt-get upgrade
when finished you should be able to install the drivers

---

### Post by jerrrys on 2010-01-30
and theirs always "ENVY" in the software center, but sounds like you already have the right driver installed or you wouldnt have a display.  i also run a dv6000 and use both 8.04 and 10.04.  in both cases i did not have to do any video driver install, it was automatic.  if you are not experiencing video problems then your good to go.  as for wireless; dont use it so cant help

---

### Post by dasThumbtack on 2010-01-30
> **halj32 said:**
> you will find the drivers for your wifi on the CD, or if your on line run in a bash shell
 sudo apt-get update
then
sudo apt-get upgrade
when finished you should be able to install the drivers

Thank you, that helped.

And Jerrrys, I need the Nvidia drivers to have visual effects. They're unnecessary, but I like 'em.

---

