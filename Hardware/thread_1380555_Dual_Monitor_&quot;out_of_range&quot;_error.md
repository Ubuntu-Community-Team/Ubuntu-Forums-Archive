---
title: "Dual Monitor &quot;out of range&quot; error"
date: 2010-01-13
forum: Hardware
---

### Post by chazwr on 2010-01-13
Greetings
Every time I log in the external monitor has an "out of rage" error. All I have to do to resolve it is change the frequency from 60 to 75 or vise versa via the Display settings. Either works fine although the 75 mhz renders a crisper image (res on both laptop and LCD = 1280 x 1024) Is there a way to avoid this every time I log in?  Setup is:

Dell Inspiron 8200 w/ Radeon 9000
View Sonic 19" LCD
Ubuntu 9.10 installed via wubi (dual boot w/ Windows XP Pro)
xorg.conf:
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Its not the end of the world, just an annoyance. Thanks for any suggestions

---

