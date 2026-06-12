---
title: "X wont start :: cant find fix on forums"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by tAK on 2005-01-07
ok, this is a WAY too common issue for you guys.... hows about someone put up a stickt thread here, with a WORKING fix... i have tried what is on here.. no luck

i think i need to install the nVidia drivers... but have NO IDEA how... please explain, what commands i need to use? i only have the consle atm....

please... help....

and once it is done... and all of the different fixes are together... make a sticky thread,.... as at least 25% of the issues here are related to X not starting after install......

oh, and why are they using the pre-release? wouldnt that be the latest version, but unstable? why not use the last STABLE version?

/tAK

---

### Post by daniels on 2005-01-07
I don't know why your X isn't starting without seeing /var/log/XFree86.0.log and /etc/X11/XF86Config-4 (I assume you are using Warty).  As for why we are using a 'prerelease', that's actually incorrect.  How we did it is complicated, but I assure you it's in no way a random unstable beta.  Most people were actually complaining because it wasn't bleeding-edge enough at the time.

---

### Post by dude2425 on 2005-01-09
try downloading it with wget:
```
wget http://download.nvidia.com/XFree86/Linux-x86/1.0-6629/NVIDIA-Linux-x86-1.0-6629-pkg1.run

```

and then installing them from there.
Alternatively you can also try using the VESA drivers instead if that don't work corectly. You can also download from a different PC, put it onto a usb thumbdrive, and install them from there if you don't have a working internet connection yet.

---

### Post by wallijonn on 2005-01-09
[http://www.ubuntuforums.org/showthread.php?t=3567](http://www.ubuntuforums.org/showthread.php?t=3567)

---

