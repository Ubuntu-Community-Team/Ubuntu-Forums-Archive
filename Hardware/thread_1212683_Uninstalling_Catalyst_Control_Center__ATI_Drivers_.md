---
title: "Uninstalling Catalyst Control Center / ATI Drivers / Dual Monitor problems"
date: 2009-07-14
forum: Hardware
---

### Post by cmmckoy on 2009-07-14
I was having problems playing games, etc. In fullscreen mode (Glest, Nexuiz, and similar games) because the screen would mess up and I wouldn't be able to see how to exit the program, let alone play it.  So I tried to update my ATI driver, and their website pointed me to installing a package for the ATI Catalyst Control Center.  I did so, and restarted my computer, and couldn't get into my computer, had to go into recovery mode, and I got my computer working by typing these three lines:

sudo apt-get --purge remove xorg-driver-fglrx

dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm restart

Which worked, but now the menu item for 'ATI Catalyst Control Center' is still there, and I don't know how to uninstall it, and when I go to System > Administration > Hardware Drivers and try to activate the 'ATI/AMD proprietary FGLRX graphics driver' it downloads okay, but when I restart my computer it will go through the loading everything with the [OK] things at the end, and stop.  The screen will flicker black a few times, then stay at the cli loading-type thing (forgive me lack of proper words, I don't quite know what their called).  I have to type those three lines above to get it to show the GUI again.

Also, the same thing occurs when I plug in a second monitor.  It seems to set up fine, but when it tells me to restart and I do so, it 'crashes'.  I can't remember exactly what it does, but I have to (again) type those three lines to get it to work.  How do I fix this so that I can use my ATI drivers and also hopefully set up dual monitors?

My specifications are as follows:

Ubuntu 8.10 (i386) on an Acer Extensa 4420:

AMD Athlon 64 x2 Dual-Core prosessor TK-57
896 MB Ati Radeon X1250 Hypermemory
2GB DDR2

Any help or suggestions would be greatly appreciated.  I've scoured the internet trying to find an answer but can't seem to find anything.

---

