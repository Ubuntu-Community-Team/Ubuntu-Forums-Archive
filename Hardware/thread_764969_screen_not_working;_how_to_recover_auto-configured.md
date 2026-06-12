---
title: "screen not working; how to recover auto-configured settings?"
date: 2008-04-24
forum: Hardware
---

### Post by lara_m on 2008-04-24
Hi everyone,

I am completely new to linux, so any help would be greatly appreciated. I have xubuntu 7.10 installed and everything worked out of the box (except for wireless, but that is solved now). I started experimenting with the "screens and graphics" settings (I wanted to keep my laptop screen from flickering while I was using the external monitor at a higher resolution) and must have somehow messed up, since now I can only boot in "safe" mode. 

How can I tell xubuntu to perform again its autodetection magic for the video/screen settings? I have tried to reproduce it manually from what I remember ("intel experimental mode setting driver", 1280x1024), but it doesn't work and reverts back to 800x600.

Any help would be great.

lara

---

### Post by pietjanjaap on 2008-04-24
sudo dpkg-reconfigure xserver-xorg 
in safe mode, choose vesa driver.
reboot then install drivers.

---

