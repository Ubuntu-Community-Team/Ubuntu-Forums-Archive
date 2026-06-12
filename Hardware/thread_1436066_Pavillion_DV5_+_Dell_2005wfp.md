---
title: "Pavillion DV5 + Dell 2005wfp"
date: 2010-03-22
forum: Hardware
---

### Post by P90Puma on 2010-03-22
Hey guys,

Trying to get my work laptop to play nice with my 20.1 1680x1050 monitor.

I am running 9.10, the laptop runs at 1280x800.

Display manager won't let me select 1680x1050 for the Dell. Just goes up to 1440x900.

My xorg.conf is as follows.

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2720 900
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "InputDevice"
	Identifier  "VX Nano"
	Driver      "evdev"
	Option      "Name" "Logitech USB Receiver"
	Option	    "Protocol" "evdev"
	Option	    "Buttons" "9"
	Option	    "SendCoreEvents"
	Option	    "HWHEELRelativeAxisButtons" "7 6"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

Thanks.

---

### Post by Yellow Pasque on 2010-03-22
> **P90Puma said:**
> SubSection "Display"
		Virtual	2720 900
EndSubSection
You have the virtual screen size set too small (900 < 1050)

---

### Post by P90Puma on 2010-03-23
> **Temüjin said:**
> You have the virtual screen size set too small (900 < 1050)

Adjusted to ```
Virtual	2960 1050
```

That let me set 1680x1050 on the second screen.

Thanks.

---

