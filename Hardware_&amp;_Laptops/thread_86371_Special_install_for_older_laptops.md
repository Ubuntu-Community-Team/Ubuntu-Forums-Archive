---
title: "Special install for older laptops?"
date: 2005-11-05
forum: Hardware &amp; Laptops
---

### Post by pilotcp on 2005-11-05
Hello Folks!

I have a compaq armada 1700, and it in a slower computer (300 Mhz, 128 mb ram)...i really just want to use it for internet, GAIM, and whatever the IRC program is (the name escapes me...is it XIRC?). I remember there was a tutorial for how do do a low memory install, but i can't seem to find one for the new releases (or the old one for that matter..i don't remember where i found it!)

Thanks,
Charlie

---

### Post by Ribs on 2005-11-06
Hi,

Try doing a clean 'server' install (type server when you boot from the install CD). When Ubuntu has installed, edit the apt's sources.list file to enable the universe repos. Then apt-get update and then apt-get install xubuntu-desktop.

XUbuntu-Desktop will install a desktop based on xfce instead of Gnome or KDE. XFCE is very lightweight, but isn't baron when it comes to features. You'll also get firefox, x-chat and Abiword thrown in. I suggest you also install gdm, as logging in and typing startx every time can get tiresome...

Good luck

PS. Also check out another thread I started yesterday. It's mainly for Toshiba Tecra users, but there are tips in there you may find usefull. Link: [http://www.ubuntuforums.org/showthread.php?p=469805#post469805](http://www.ubuntuforums.org/showthread.php?p=469805#post469805)

---

