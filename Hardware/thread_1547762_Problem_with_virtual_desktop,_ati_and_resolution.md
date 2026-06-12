---
title: "Problem with virtual desktop, ati and resolution"
date: 2010-08-07
forum: Hardware
---

### Post by TheBestNeo on 2010-08-07
Hello, i don't know why when i'm at login screen my desktop is large double than i had set (1440).

For fix this, i must change resolution and then re-change to 1440x900. 
I've tried many xorg configuration, but it does'nt fix the problem.

When i delete xorg it works, but i don't have 3d, effects and many more.

I have ati driver on Karmic, i don't know which thing do this.

My xorg:
```

Codice:
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes   "1440x900_60.00"
		Virtual 1440 900
		Option "PreferredMode" "1440x900"
	EndSubSection

EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Extensions"
	Option "Composite" "Enabled"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

#Section "ServerFlags"
#	Option "AIGLX" "Off"
#EndSection

```

This was last try, i've tried to do an aticonfig and make a minimal xorg too, but whit no results.

---

### Post by TheBestNeo on 2010-08-08
Resolved. I've uninstalled and reinstalled ati driver.

---

