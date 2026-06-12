---
title: "Cant get Debian to boot"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by fungihead on 2009-02-28
I want to try debian. I have it installed ok but when i try to boot i get a "Monitor out of range" message from my monitor. Im pretty sure this means that the default setting for x is below my monitors refresh rate range (in windows i can get 60hz - 75hz)

Ive googled a bit and found that i can add lines into the xorg.conf to make it boot, which i tried but it didnt work. What i figured i would try was to live cd into ubuntu which works first time with my monitor and just copy the xorg.conf.

when i looked at it tho the .conf file from ubuntu is EXACTLY the same as the one in debian, and yet x works in ubuntu and not in debian

what am i missing? maybe a driver or something?

anyone know the apt-get for it? nvidia card

---

### Post by albinootje on 2009-02-28
> **fungihead said:**
>  when i looked at it tho the .conf file from ubuntu is EXACTLY the same as the one in debian, and yet x works in ubuntu and not in debian 

Are you trying Debian Lenny or Debian Etch ? Etch is pretty old for a desktop now.

And if you know the specifications of your monitor, then you can generate a ModeLine and put that in /etc/X11/xorg.conf : [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

### Post by fungihead on 2009-03-01
lenny i think (debian 5)

il give that modeline generator a go

---

