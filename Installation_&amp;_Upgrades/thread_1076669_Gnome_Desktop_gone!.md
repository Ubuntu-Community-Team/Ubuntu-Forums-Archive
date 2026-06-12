---
title: "Gnome Desktop gone!"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by gazzatav on 2009-02-21
Ubuntu 8.04

After having loads of problems with network-admin giving me a greyed-out unlock button and not being able to get internet connection (Winxp is fine on another partition), I decided to uninstall policykit as forum searches had the policykit as the problem.  Um, now I don't have the Gnome desktop as default when I log in, I get KDE 3.5.  How do I get the Gnome desktop back?

---

### Post by Partyboi2 on 2009-02-21
Open a terminal and
```
sudo apt-get install ubuntu-desktop
```
this should pull in any packages that are missing.

---

### Post by gazzatav on 2009-02-23
Thanks Partyboi2, I've tried that but without the internet connection it can't pull in the packages (even though the ones it was using before must still be present as I only uninstalled them, I didn't remove them).  There seems to be a big problem with ethernet since a recent update (not just with me).  It seems I need to get the internet connection working again under KDE before I can restore the ubuntu desktop.  I've tried to set the ip address with ifconfig but I just get unknown host.

---

### Post by gazzatav on 2009-02-23
Fixed it!

If anyone else is having trouble with network-admin try using ifconfig and route.  It took me a couple of goes but the result was worth it.

eg. sudo ifconfig eth0 192.168.0.xx or address on router ip range.
then sudo route add default gw <gateway address>

---

