---
title: "External monitor to the left"
date: 2009-04-14
forum: Hardware
---

### Post by Dooley on 2009-04-14
Hey all,

I use openbox with ubuntu. My external monitor worked perfectly without modifying xorg all I did was plug it in. However due to an office move the monitor has to go to the left of my laptop screen. So I'm wondering how I change xorgs config so that when I move my mouse to the extreme left it will go to the external monitor.


Here's my xorg config.
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2384 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```


Thanks!

Dooley

---

### Post by Dooley on 2009-04-14
Sorry, I actually solved it myself with ubuntus awesome screen resolution app.

Thanks anyway. :D

---

