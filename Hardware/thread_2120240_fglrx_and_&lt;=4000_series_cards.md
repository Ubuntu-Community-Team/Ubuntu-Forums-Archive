---
title: "fglrx and &lt;=4000 series cards"
date: 2013-02-26
forum: Hardware
---

### Post by cob on 2013-02-26
I am using the on-board GPU in my machine, it's a Radeon 4200.  There was a point in time that I could actually play videos smoothly, without tearing, and had HDMI working - with audio even!  It seems like with regard to this hardware, Ubuntu regresses with each release.

Enough ranting though, what is the status of support for these GPUs in the fglrx world?  I'm using "radeon" right now, but it's terrible.  Videos are tearing, Flash is awful and actually causes my mouse to lock up frequently, the Unity desktop is barely usable.

Hoping there are answers out there!

---

### Post by QIII on 2013-02-26
This may be an issue with your version of Ubuntu and whether the ATI driver will work with it.  (Not a regression in Ubuntu.)

Which version of Ubuntu are you using?

---

### Post by Yellow Pasque on 2013-02-26
The status is that fglrx will work fine in Ubuntu 12.04, but takes a little hacking to get working with Ubuntu 12.10. The first thing you should do is make sure open source driver is installed correctly What is output of glxinfo?
```
sudo apt-get install mesa-utils
glxinfo
```

/var/log/Xorg.0.log could be helpful too.

---

