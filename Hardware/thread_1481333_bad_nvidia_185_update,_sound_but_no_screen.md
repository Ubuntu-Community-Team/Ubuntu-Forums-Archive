---
title: "bad nvidia 185 update, sound but no screen"
date: 2010-05-12
forum: Hardware
---

### Post by Toast2120 on 2010-05-12
Just installed 9.10 after not getting anywhere with 10.04. Decided to run the Nvidia restricted drivers. Installed the 185 as recommended. Saw the Ubuntu logo at boot, then nothing, blank screen. I know the system booted as I can hear it start up and when I logged in.

Restarted. Now in low graphics mode, gonna drop some code to see if anyone can get me to working again.

Here is my xorg.conf right now

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

Here is xorg.conf.failsafe
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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

The xorg.conf-backup-100512115642 is the same as xorg.conf. Drivers as obviously installed but not working.

My system is
athlon 4200
2 8800 GTS 512 SLI
2 GB RAM

I'll be here all day it seems. Just wanna get back to working mode.
How to make drivers work?
How to uninstall drivers?

Either is fine by me.

---

