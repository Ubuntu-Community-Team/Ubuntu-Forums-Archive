---
title: "Installation problems with x800xl bit depth"
date: 2005-12-21
forum: Installation &amp; Upgrades
---

### Post by jimchristopher on 2005-12-21
I'm having problems getting 5.04 or 5.10 on my system, Shuttle SN35P nForce4 Athlon64 3200 ATI X800XL.  After installation, I get dumped to a black screen with an error about not being able to load X.  I have tried several "fixes" like apt-get fglrx and sudo dpkg reconfigure.  Everything is detected correctly if I autodetect, but whether I autodetect or not I always get dumped to the terminal with this error:

xserver-xorg postinst warning:  overwriting possibly-customised configuration file: backup in /etc/X11/xorg.conf .200512202132

it doesnt matter if I choose ATI, vesa, vga and Ive tried all bit depths 1-24.  

I've followed a couple of ATI drivers wikis but to no effect.  it installs and runs fine on my nforce2 NV6600GT.

---

### Post by jimchristopher on 2005-12-23
got it running, after installing the xorg-driver-fglrx and running fglrxconfig, I edited the xorg.conf file and added the AGPGART "no" option.  but I'm also having trouble with not being able to reboot except at the terminal.  I think I saw a fix for that somewhere around here...

---

