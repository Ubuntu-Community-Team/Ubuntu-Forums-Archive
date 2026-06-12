---
title: "3D Labs Wildcat III 6110"
date: 2008-09-03
forum: Hardware
---

### Post by Max-B on 2008-09-03
Hi,
I would like to install Ubuntu 8.04 on my workstation. Does anybody knows if my 3DLabs Wildcat III 6110 graphic card will be supported?
Ciao,
Max

---

### Post by komputes on 2009-09-03
You will have no luck running a 3DLabs Wildcat III 6110 on Ubuntu. I have tried on every release from 7.04 to 9.10 and there is nothing which works. The LiveCD does not work, the alternate install works but no graphical desktop. You will only get a red display when trying to boot X. Not even VESA mode works with this card. However if you want to use it as a server, the VT (virtual terminals) show up fine. Yay command line! :D

This was filed as bugs on launchpad (wontfix) and freedesktop.org (new,2004):
[https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/370654](https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/370654)
[https://bugs.freedesktop.org/show_bug.cgi?id=1907](https://bugs.freedesktop.org/show_bug.cgi?id=1907)

3dlabs has closed source (binary) drivers available for various Oxygen and Wildcat based cards, but this is from 2004, for older 2.4 kernels and most likely for XF86 and not Xorg (two different visual server for graphical desktops).

[http://www.3dlabs.com/support/drivers/](http://www.3dlabs.com/support/drivers/)

You see, up to about 2004, an implementation called XFree86 provided the most common X variant on Linux systems. XFree86 started as a port of X for 386-compatible PCs and was the most popular X implementation on Linux for several years.

Since 2004, however, the X.org reference implementation, (originally a fork of XFree86), has become predominant. It is used by all modern Linux distributions, including Ubuntu.

The X.org server supports almost all modern graphics hardware. Since the source to these XFree86 binary drivers were never released there is little to no chance that this card will be supported in Linux.
The easy solution, go out and get an nvidia video card.

---

