---
title: "Desktop effects cannot be enabled in 9.10 RC... is this normal?"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by the8thstar on 2009-10-27
I use a 945 intel graphics card. I upgraded to 9.10 RC and now the desktop effects can't be enabled anymore. Is this a transition problem or this yet another case of poor support for Intel chipsets?

Thanks for your help.

---

### Post by BigG123 on 2009-10-27
No, they work for me.  Try going to System > Administration > Hardware Drivers.   Activate graphics drivers.

---

### Post by howefield on 2009-10-27
> **the8thstar said:**
> I use a 945 intel graphics card. I upgraded to 9.10 RC and now the desktop effects can't be enabled anymore.

Getting to be an annual thing for you ;)

Couldn't be the answer here ? 

[http://ubuntuforums.org/showthread.php?t=947230](http://ubuntuforums.org/showthread.php?t=947230)

---

### Post by the8thstar on 2009-10-27
Good call **howefield**! You seem to keep better track of things than I do!

Anyway, I tried my old trick, and here is the difference between the new and the old xorg.conf

NEW :

> [COLOR="Blue"][B]Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true"
EndSection[/B][/COLOR]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

OLD:

> 
[B][COLOR="Blue"]Section "Device"
	Identifier	"Configured Video Device"
EndSection[/COLOR][/B]

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

So... what do I do with the new options?

---

### Post by the8thstar on 2009-10-28
I replaced the new xorg.conf with the old one. No joy. Desktop effects still can't be enabled. Darn.

Anyone has a solution for this? For the record, I upgraded to 9.10 on my old P4 with an 256Mb nVidia gfx and desktop effects run more smoothly than ever. So I'm puzzled as to what to do next.

---

### Post by the8thstar on 2009-10-30
All my problems came to an end with a fresh install!

---

