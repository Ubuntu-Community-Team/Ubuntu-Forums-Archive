---
title: "use remastersys without installing nautilus, other apps, etc"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by pythonscript on 2009-07-24
I'm trying to use remastersys in the way intended: to make a custom iso from my ubuntu installation. However, when I install remastersys, it pulls in a large number of gnome programs. So.... I use

```
sudo apt-get install remastersys --no-install-recommends
```to stop that. However, it keeps pulling in nautilus and a few other gnome apps. Since I'm using a ubuntu installation that uses icewm as a simple, *optional* window manager (the os only loads the command line at boot) I don't want nautilus, or anything gnome-related. I only want an iso of my current installation, with as little extra junk installed with remastersys as possible. How can I do this? I'm trying to keep this within CD size, too, so all the added stuff is a real problem.

EDIT:  Solved in a different thread. I'll post it here for archival purposes. [http://ubuntuforums.org/showthread.php?t=1216130](http://ubuntuforums.org/showthread.php?t=1216130)

---

