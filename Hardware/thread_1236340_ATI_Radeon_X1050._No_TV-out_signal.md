---
title: "ATI Radeon X1050. No TV-out signal"
date: 2009-08-10
forum: Hardware
---

### Post by tibia_fry on 2009-08-10
Hello, I have an ATI Radeon x1050 connected via s-video+scart adapter to a TV. When the system is starting I can see the signal on the TV but once on ubuntu I can't see any signal on the TV (totally black, like shut down).

I'm not a linux pro, so I would appreciate a step-by-step guide. Also note that I've tried tons of options on forums etc without much luck. Using "Display preferences" -> "Detect monitors" doesn't work neither.

On Windows I can see the image but on black and white, so I decided to try Ubuntu for that.

Any help would be terribly appreciated. Thanks

[QUOTE=my xorg.conf]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection[/QUOTE]

---

### Post by tibia_fry on 2009-08-10
bump please help me-

---

### Post by tibia_fry on 2009-08-12
I need help. Please someone?

---

