---
title: "Cannot use widescreen (1440x900) resolution in 10.04"
date: 2011-02-08
forum: Hardware
---

### Post by pd_ on 2011-02-08
I have recently moved to Ubuntu 10.04 lucid, and after a lot of configuring in xorg.conf, mainly guided by this thread [http://ubuntuforums.org/showthread.php?t=280683](http://ubuntuforums.org/showthread.php?t=280683) , I eventually managed to get my 1440x900 @ 60Hz resolution working on my Samsung Syncmaster 943NW screen, using a ATI Radeon HD 4850 and the proprietary drivers (Catalyst) which I *manually* installed.

So far so good. Yesterday I finally got an internet connection and I performed an update of Ubuntu. That asked me to restart, and it seems as if it re-installed the graphics drivers and everything was back to 1024x768 again - great!

And to make matters worse, now I cannot get my 1440x900, which, btw, is the monitor's native resolution, hacked in at all. Both the Catalyst Control Center and GNOME's "Monitor Preferences" offer me a maximum resolution of 1280x1024.

I've tried adding a Modeline to the "Monitor" section and adding it to the "Screen" in xorg.conf, nothing.
I've tried adding the ModeValidation option "NoEdidDFPMaxSizeCheck", nothing.
I've tried modifying *~/config/monitors.xml*, which yielded a message that the resolution is not supported, as expected.

Basically I did everything that did help *before* I updated, but now I can neither get 1440x900 listed in the ATI CCC, nor can I force it somehow.

Now I'm totally out of ideas. I've attached my current xorg.conf, I hope somebody can help. I would greatly appreciate it, thanks in advance!

---

### Post by ajgreeny on 2011-02-08
You may simply need to install the catalyst driver again now, as I suspect there was a new kernel in your updates.

---

### Post by pd_ on 2011-02-09
I just disabled the "proprietary driver" and downloaded the drivers from the ATI website and reinstalled those (I had them before).

They are installed correctly (fglrxinfo reports the correct GPU etc.), I added the modelines again, set my desired resolution as PreferedMode, disabled the EDID check, no luck. I cannot make 1440x900 appear anywhere, at all.

What information sources are used to determine the "available" display modes?
Is there no way to simply force a certain resolution? I think the modelines settings are meant to achieve this, but they have absolutely zero effect.

---

