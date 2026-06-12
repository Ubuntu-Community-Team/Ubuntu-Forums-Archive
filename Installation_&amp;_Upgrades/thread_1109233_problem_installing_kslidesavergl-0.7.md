---
title: "problem installing kslidesavergl-0.7"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by quantock48 on 2009-03-28
Hi,

I am a new Ubuntu user and a new member of this community.

I have Intrepid Ibex and am using KDE.

I am currently trying to install kslidesavergl-0.7 and I have hit a roadblock.  When I enter the command:
> ./configure
I get the following error:

> checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.


config.log wasn't much help.  I looked at old forum threads on similar problems, but cannot find one that includes a solution I haven't already tried.

I have installed the following additional packages to no avail:
libqt3-mt
libqt3-headers
libqt3-compat-headers
libqt3-mt-dev
kdebase-dev
gtk-qt-engine
qt3-dev-tools
libavahi-qt3-dev
qt3-dev-tools-embedded
qt3-designer
qt3-apps-dev
qt3-assistant
qt3-qtconfig

and a few more!

Does anyone have any ideas?

Thanks

---

### Post by Partyboi2 on 2009-03-28
Try installing kdelibs-dev package

```
sudo apt-get install kdelibs-dev
```
then use

```
./configure  --with-qt-includes=/usr/include/qt3/ 
```

---

### Post by quantock48 on 2009-03-29
Thanks for the quick reply.  That did indeed solve that problem.  However, I now get a whole slew of errors when I run make.  Seriously thinking of giving up on this one.  Not sure if it's worth the effort for a screensaver!  I don't believe I said that!  :confused:

---

