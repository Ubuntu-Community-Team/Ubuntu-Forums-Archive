---
title: "Kernel upgrade to 2.6.27-11 = no gnome display"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by DesertFox34 on 2009-02-09
Hi,

I've been having this problem for the past two kernels (2.6.27-9 and 2.6.27-11). I can install the new kernels from update manager without problems. However I get no gnome display on boot to the new kernels. Pressing the power button does say 'Stopping Gnome Display...' and shuts down.

Current (and only) kernel that works - 2.6.27-7
Graphics - ATI Radeon HD 3200
Proc - AMD 64Bit

```
# xorg.conf (X.Org X Window System server configuration file)

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

I've tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` But it only works once and on restart it does the above.

So anything I can do to fix this? It's just annoying sticking to a few months old kernel.

-Fox

---

### Post by TheNinjaPirate on 2009-03-15
Bump: I'm having the same problem, except 2.6.26-11 is the last one that works for me.Anyone have an idea?

---

