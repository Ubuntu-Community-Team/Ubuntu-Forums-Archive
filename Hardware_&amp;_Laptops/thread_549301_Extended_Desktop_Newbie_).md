---
title: "Extended Desktop Newbie :)"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by aaronthebear on 2007-09-12
**[SIZE="4"][COLOR="Orange"]Hey Everyone on the UbuntuForums :)[/COLOR][/SIZE]**
I have  recently bought a Samsung 225mw 22" monitor for TV and extended desktop goodness with my laptop (HP Pavilion Dv1000 series)
I have extended desktop running great in my Windows XP Home partition, but being quite new to Linux, ubuntu 7.04 especially, i have absolutely no idea how to create an extended desktop :(

All i have tried so far is to plug in the monitor into my VGA port and boot to see what happens. Ubuntu boots as normal and on my external monitor i get a copy of what's on my laptops screen in the same resolution, but a bit off screen. I had a good look through the "preferences" and "Administration" menu's but can't find anything about dual-monitors setups :)

If anyone can help me with this i would appreciate it :), I've become so used to dual monitors in Windows, i feel lost in ubuntu right now :) Thanks!

If you need to know my computers specs here they are:

[B]Hp Pavilion DV1066ea
Intel 82852/855GM Integrated Graphics (64mb shared memory)
1GB RAM

External Monitor is a Samsung 225MW 22" with resolution of 1680x1050 on VGA

I don't know if this will affect it in any way, but i have compiz-fusion installed.

Thanks Again :)[/B]

---

### Post by frith on 2007-09-12
Hmmm no nVidia card, this could be interesting.

I know that the binary nVidia drivers support extended desktops using TwinView, but I've not had any experience with anything else. I've had a lot of pain trying to get my monitor configuration 'just right' (something that was laughably easy in windows shouldn't be so hard in Ubuntu IMHO).

There is hope:
[http://www.linux.org.au/conf/2007/talk/95.html](http://www.linux.org.au/conf/2007/talk/95.html)
[http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)

There is no good reason why you shouldn't be able to get it to work, the real issue will be one of time and knowledge invested. Try searching around a bit for dual/external monitors in Ubuntu, you might get lucky...

Frith.

---

### Post by JC Casiano on 2007-09-12
Go to the Control Center or System Settings, find Monitor & Displays (under Peripherals).  If your adapter will support more than one monitor you should be able to configure it from there (need to go into Administrator mode).  The tab you want first is "Hardware".

CAUTION: make a backup copy of /etc/X11/xorg.conf before you do anything, I've wiped out my custom configuration more than once.

---

