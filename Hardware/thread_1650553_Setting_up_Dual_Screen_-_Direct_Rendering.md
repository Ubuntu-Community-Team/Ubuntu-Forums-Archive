---
title: "Setting up Dual Screen - Direct Rendering"
date: 2010-12-21
forum: Hardware
---

### Post by allinurl on 2010-12-21
I'm trying to set up dual screen on my Ubuntu 9.10, I have an ATI Firegl v7100, stock ubuntu installation. I have not yet installed any additional drivers, but I'm getting direct rendering already.

Does anybody knows how to setup dual screen based on my current xorg.conf (1680×1050, 1280×1024)

Any help it is appreciated!

```
glxinfo | grep rendering
direct rendering: Yes
```

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```
Thanks

---

### Post by Fir3chi3f on 2010-12-21
Hmm, well I know that the old ati proprietary drivers are not supported by ati anymore and I believe that they are left to the community. So that should explain why you have direct rendering. 

I don't think ubuntu likes using the xorg file, but when I set up multiple monitors with my nvidia 8800gs the official nvidia tool did just reconfigure the xorg file. I'll post back if I can figure out what it put in there.

---

### Post by Fafler on 2010-12-22
Fir3chi3f is right about the driver. You are stuck with the Open Source driver, which is not perfect, but it works. Follow the ATI part of this guide to make a working xorg.conf: [https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)
Replace the resolutions to match your monitors.

---

