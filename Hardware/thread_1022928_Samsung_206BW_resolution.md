---
title: "Samsung 206BW resolution"
date: 2008-12-27
forum: Hardware
---

### Post by hidarikani on 2008-12-27
I just switched to 8.10 and enabled the non-free Nvidia drivers.
The highest resolution available is 1024x756 but it has to be 1680x1050.
So I manually edited my xorg.conf to look like this:
```

Section "Monitor"
        Identifier  "206BW"
        Horizsync   30-81
        Vertrefresh 56-75
        ModeLine    "1680x1050@65" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	DefaultDepth	24
        SubSection "Display"
                Depth  24
                Modes  "1680x1050"
        EndSubSection

EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

After that I rebooted and guess what, nothing changed: I'm still stuck with 1024x756. Looks like xorg.conf is being ignored. How do I set a proper resolution? Please help.

---

