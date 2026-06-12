---
title: "Why does Xubuntu want me to install ATI drivers? 12.04"
date: 2013-04-30
forum: Hardware
---

### Post by Scozzar on 2013-04-30
Hi all, I just installed bumblebee and the Nvidia drivers after coming from 13.04.  I run "optirun glxspheres" and it all works, however, the update manager is wanting me to install the following:

_Other Updates LP-PPA-ubuntu-x-swat-x-updates_

X Acceleration library - runtime
X.Org X Server - AMD/ATI display driver wrapper
X.Org X server - Intel i8xx, i9xx display driver
X.Org X server - Nouveau display driver
X.Org X server - AMD/ATI display driver



Now during the installation of Bumblebee, it said that versions 11.04 and earlier didn't have to install the x-updates PPA, but I did any way.  I have an Nvidia graphics card so I am not sure why it's asking me to download ATI drivers.  Help?

EDIT:  It seems that removing the PPA for X-swat removed the updates.  Case solved?

EDIT 2:  GAH!  The Nvidia X server settings don't work!  I get the usual ```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

---

