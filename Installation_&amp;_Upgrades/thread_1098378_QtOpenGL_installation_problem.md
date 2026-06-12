---
title: "QtOpenGL installation problem"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by bijay_panda on 2009-03-17
Hi,
I am using ubuntu 8.04.I installed Qt4.4.3.In the Qt doucumentation,it's written that QtOpenGL will be there by deafult when we install qt full frame work.I did the same from synaptic package manager,but not getting QtOpenGL package only.All other packeges are there in usr/include except QtOpenGL.I tried sudo apt-get install libqt4-opengl but it's showing message that latest version is there like bellow.

libqt4-opengl is already the newest version.
The following packages were automatically installed and are no longer required:
  libepc-ui-1.0-1 libsigc++-2.0-dev x11proto-xext-dev libepc-1.0-1 libaudio-dev libglib2.0-dev x11proto-xinerama-dev
  x11proto-render-dev libxi-dev libxmu-headers libxrender-dev mesa-common-dev libglu1-xorg-dev libgalago3 libsqlite0-dev
  libfontconfig1-dev lib64gomp1 libxcursor-dev libglu1-mesa-dev libglibmm-2.4-dev x11proto-randr-dev libxmu-dev libxext-dev
  libfreetype6-dev x11proto-fixes-dev libgl1-mesa-dev liblcms1-dev libxrandr-dev libgmyth0 libxft-dev libxfixes-dev
  libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1068 not upgraded.


I m running projects of qgis also,if i will choose remove and reinstall then some libraries will be removed from qgis also.
what should be the best procedure to get rid of this.
Any help is appreciated.

Thanks in advance
Bijay.

---

### Post by Johees on 2009-04-21
I'm having the same problem with QtOpenGL not found in the /usr/include directory.
I want to install a application (QLandkarteGT) from source and need to use Cmake for this. Cmake can't compile because it needs to find the QtOpenGL in /usr/include

This is the first time I've tried to install something from source code, so all this is pretty new to me.

Have you solved this problem yet? If you have, I would appreciate any help.

Thanks!

---

