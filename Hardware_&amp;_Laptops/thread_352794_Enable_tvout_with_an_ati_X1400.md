---
title: "Enable tvout with an ati X1400"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by KLineD on 2007-02-03
Hello everyone!

I'm trying to get my laptop's tvout to work. The tvout is a svideo one and the graphics card is an ati X1400. I'm using fglrx driver. I already tried to boot the laptop with the tv connected to the svideo output but still nothing. I'm using Edgy Eft and also (don't know if it's important) XGL/Beryl

What I have done so far is to use aticonfig, but I get an error:

> 
cesar@frodo:~$ sudo aticonfig --enable-monitor=lvds,tv
ati_dm: FGLRX_EnableDisplays failed when try to enable display: 6.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-7


I tried with --force-monitor and restarted and nothing. Also I tried manually editing xorg.conf and the only thing I got was no output in the laptop display (but the os was functioning properly, I could hear sounds, login, etc but I couldn't see anything) but also no output in the tv.

Has anyone managed to get this to work? If it is a driver issue, could I use the open source driver just to get the tvout to work and then switch to fglrx when I'm done?

Thanks!

---

