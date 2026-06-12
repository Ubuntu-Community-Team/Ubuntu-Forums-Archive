---
title: "gdm problems after updates"
date: 2008-08-04
forum: General Help
---

### Post by plesset on 2008-08-04
Once again I'm having Gnome related issues after updating my system (Ubuntu 8.04, running on a Asus A6VM-A laptop, 2.6.24-19-generic). When I reboot the machine it starts up but goes to a terminal display (i.e. not the orange progress bar) and starts loading files necessary for booting. Everything seems to be progressing normally, but I get a warning when starting the gdm (version 2.20/7) that a "unknown terminal 'linux'" has been detected and finally the boot hangs after "running local boot scripts". Alt-F1 allows me to log in and everything seems fine. I can't start X (via startx). I tried to reconfigure the xserver via dpkg reconfig-xserver but it failed. Finally I uninstalled the Nvidia driver and rebooted. The result was the same. Should I try to remove gnome and reinstall? What would be the best way to do that?

---

