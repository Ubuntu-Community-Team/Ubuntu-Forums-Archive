---
title: "Kubuntu 64 bit  - Ati Driver problem"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by Fixxer on 2005-07-19
Hi,

hope it's the right forum

ive tried to install the ati driver for Kubuntu 64bit. it all worked fine, but i have the problem, that the x-server don't want to use the fglrx driver.

But first my installation steps

Kernel-version 2.6.10-5-amd64-generic
X - version: 6.8.2

Installation
- install kernel headers for my kernel and gcc
- download the driver .rpm package for my x-xerver and kernel-version from the ati-site
- use alien to change it into a .deb package
- dpkg -i --force-overwrite on the package, works fine
- init 3
- lsmod | grep fglrx -> module was loaded
- cd /lib/modules/fglrx/build_mod -> sudo sh make.sh, works also fine, only one file  has to be created by the script
- cd /lib/modules/fglrx -> sudo sh make_install.sh, works also fine, no errors
- init 5
- sudo kedit /etc/X11/xorg.conf -> replace at the driver line the name "ati" with "fglrx"
- restart system
- fglrxinfo -> opengl-driver: mesa project... :(

then i tried to use the fglrxconfig to create a new xorg.conf, restart system but when I type fglrxinfo, i get the same output as below
Tried also du reconfigure the xserver vie dpkg-reconfigure xserver-xorg, there i select the fglrx driver, then restart system but the same problem as below, opengl driver: mesa project....

how can i get the ati driver work on my system? any ideas
lsmod | grep fglrx says the driver is loaded but why X don't use it?

thx 4 hlp Fixxer

---

### Post by Fixxer on 2005-07-20
nobody, who have an idea? :(

---

