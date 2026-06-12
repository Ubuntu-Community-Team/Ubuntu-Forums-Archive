---
title: "Problem with xorg.conf when used with nvidia-settings"
date: 2009-07-08
forum: Hardware
---

### Post by RJARRRPCGP on 2009-07-08
Xorg.conf hardly has anything with a 100 percent fresh Jaunty Jackalope installation:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

The problem is that saving changes failed with these errors and a segmentation fault occurred: (I never had one in at least a long time!)

```
VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Segmentation fault
```

[http://ubuntuforums.org/showthread.php?p=7585239#post7585239](http://ubuntuforums.org/showthread.php?p=7585239#post7585239)

---

### Post by shatterblast on 2009-07-09
Jaunty is taking a design practice of steering average users away from xorg.conf.  In a few cases of compatibility with input devices, it still remains necessary.  Most of those settings are shifting to other device drivers.  The benefit comes in improved ease of use.  A few of the new technologies require negotiation still.

In regards to nVidia drivers, why not just update the drivers?  You can download "envyng-qt" from Synaptic if it helps.

---

