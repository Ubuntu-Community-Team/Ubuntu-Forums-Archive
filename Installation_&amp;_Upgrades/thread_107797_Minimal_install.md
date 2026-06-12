---
title: "Minimal install"
date: 2005-12-24
forum: Installation &amp; Upgrades
---

### Post by maaylix on 2005-12-24
Hey there, I want to know if I can customize my Ubuntu install (using a Breezy cd) by going through server install

I want to install gnome-core and use the xorg fglrx driver. I don't know how I'd do this. I'm guessing that I would need to install xorg then install gnome-core with gdm like this:

After server install, loging on as root I would type:

apt-get install xorg-common
apt-get install x-window-system-core
apt-get install xserver-xorg
apt-get install xorg-driver-fglrx (I don't know if this would be necesary)
apt-get install gnome-core 
apt-get install gdm

After rebooting would I get gnome-core running with my Radeon 9600 with 3d aceleration?

Corrections, sugestions, comments are very welcome :mrgreen:

---

