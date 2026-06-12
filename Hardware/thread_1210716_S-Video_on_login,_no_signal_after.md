---
title: "S-Video on login, no signal after"
date: 2009-07-11
forum: Hardware
---

### Post by cabosixpack on 2009-07-11
Hi, I'm kind of new with ubuntu, this is my third try to completely migrate from windows xp, first try with ubuntu 7, then 8 and now with 9.

I'm 90% done, i even got to install MS office 2007 in ubuntu, which is vital for my job.

Now, the 1 use i have for my laptop as far as for personal entertainment. I have riped every single movie I own, and have it on a external drive, and i love it, so not being able to send the s-video signal to my tv, is almost enough for me to come back to windows, so PLEASE save me from the darkside.

I'm on a HP pavilion dv2535la, with a i945 graphics. When I turn on the laptop with the s-video pluged in, i see the login screen on the tv, with no problems, as soon as I login no signal, and no way to send it from System>pref>display settings.

This is my xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1024 1536
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" 
EndSection
```

thanks for the help

---

### Post by cabosixpack on 2009-07-12
Is there maybe a more appropriate forum for this?

---

### Post by cabosixpack on 2009-07-12
bump

---

### Post by cabosixpack on 2009-07-13
Never mind, solved by upgrading to kernel 2.6.30

---

