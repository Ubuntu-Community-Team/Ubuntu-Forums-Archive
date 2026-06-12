---
title: "Install trouble on old PC"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by marcan on 2005-12-26
I'm trying to install 5.10 on a friend's old P90 (40-something MB RAM) to use mainly as a server, but which he would like to have a GUI on too, since he doesn't yet find his way around the commandline.

The (normal, not server mode) installation proceeds fine (in low-mem mode though), but when I get to the point where it tells me it will reboot and install more packages, it just reboots into a console login. Just before the console login it spends some time with a blank screen, cursor blinking on the upper left corner (after running the init scripts, which complete fine), but I see no error or message. Is this normal behavior, or have I missed something obvious? Maybe the install is aborting for some unknown reason and just proceeds to the login prompt? The system seems to be missing many (non-required, but useful) packages, and of course there is no GUI or Xserver (it doesn't even have the man command). I guess I can continue installing packages manually (Previous to reinstalling, I tried and succeeded in installing xfce4), but just manually installing everything is a major PITA (unless I can at least use some meta-package or script that will do whatever the installer was going to do)

Any help would be appreciated.

---

### Post by viaciofano on 2005-12-26
i have loaded the server version and as i am new to linux found it hard as only the command line is seen...
Vinny

---

### Post by Sef on 2005-12-26
Here is the link to a page about doing an installation of a low memory system:

[https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28memory%29]("https://wiki.ubuntu.com/Installation/LowMemorySystems?highlight=%28memory%29")

When do installing in the server mode install fluxbox, a light weight window manager:

> sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

This is the lightest installation possible, which uses Fluxbox as its window manager. 

---

