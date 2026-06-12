---
title: "[SOLVED] intrepid: flashing display with radeon9600"
date: 2008-11-20
forum: General Help
---

### Post by greenshirt11 on 2008-11-20
Oops: just found [https://bugs.launchpad.net/bugs/278471]("https://bugs.launchpad.net/bugs/278471") that seems to describe the same problem and the solution:
-> turnoff "Detecting RANDR (monitor) changes" in "startup services".
That worked!
----------------------------------------------------------------------------

Installed Intrepid but every 10 seconds or so the screen briefly flashes.
My graphics card is an ATI Radeon-9600. Worked ok in Feisty.
Also every 10 seconds some messages are logged in /var/log/xorg.0.log:
```
	Informatie	RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
	Informatie	RADEON(0): I2C device "VGA-0:ddc2" removed.
	Informatie	RADEON(0): Output: VGA-0, Detected Monitor Type: 0
	Informatie	RADEON(0): Found color CRT connected to primary DAC
	Informatie	in RADEONProbeOutputModes
	Informatie	RADEON(0): Adding Screen mode: 1152x864
	Informatie	RADEON(0): Adding Screen mode: 1024x768
	Informatie	RADEON(0): Adding Screen mode: 1024x768
	Informatie	RADEON(0): Adding Screen mode: 800x600
	Informatie	RADEON(0): Total number of valid Screen mode(s) added: 4
	Informatie	RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
	Informatie	RADEON(0): I2C device "DVI-0:ddc2" removed.
	Informatie	RADEON(0): Output: DVI-0, Detected Monitor Type: 0
	Informatie	RADEON(0): Output: S-video, Detected Monitor Type: 0

```
I already adapted my /etx/X11/xorg.conf but that doen't help (see attachment).
Does somebody have a clue on how to proceed with this?

Thanks,
Folkert

---

