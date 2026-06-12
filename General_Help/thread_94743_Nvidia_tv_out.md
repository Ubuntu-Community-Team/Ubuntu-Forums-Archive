---
title: "Nvidia tv out"
date: 2005-11-24
forum: General Help
---

### Post by shockertwin on 2005-11-24
Ok so i was attempting to follow a tv out toturial tha ti saw earlier, but apparently i can no longer get nvtv. How do i get tv out working on Ubuntu 5.10. Thanks.

Oh i use a geforce 6600

---

### Post by BigMurph on 2005-11-24
You can still get nvtv at SourceForge ([http://sourceforge.net/projects/nv-tv-out](http://sourceforge.net/projects/nv-tv-out))

You can also use TwinView, which you have to enable in your Xorg.conf file. You need the proprietary driver from the Nvidia website, and the documentation there should help get you started.

In short you have to add the following lines to your device section in xorg.conf:

Option "TwinView" "on"
Option "TwinViewOrientation" "Clone" (or "LeftOf", "RightOf", etc)
Option "SecondMonitorHorizSync" 30-50
Option "SecondMonitorVertRefresh" 60

I'm not completely sure of the option names and values, so checking the documentation would be a good idea...;-)

---

