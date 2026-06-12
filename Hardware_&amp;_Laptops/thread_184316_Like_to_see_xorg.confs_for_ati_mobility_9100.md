---
title: "Like to see xorg.confs for ati mobility 9100"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by towsonu2003 on 2006-05-29
If you have an ati mobility 9100, can you post / attach / paste it here? I'd like to see what other xorg.conf files look like for this stupid card. 

Thanks :)

PS. Exact card I have is: 
ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)

---

### Post by transactionlogfiller on 2006-05-29
I think that's the exact same card as mine. I have a desktop which spans 2 monitors though, the laptop screen and an external tft.

These are the display related bits:
```

Section "ServerLayout"
	Identifier     "Widescreen-Dual"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "RadeonCard"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "DesktopSetup" "horizontal,reverse"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "RadeonCard"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

You might want to use the ati driver instead of fglrx, and lose the 'Option	    "DesktopSetup" "horizontal,reverse"' bit if you only have one monitor.

Hope that helps.

---

### Post by towsonu2003 on 2006-05-29
thanks :) what does your "Modules" section look like? 

in the meantime, let me attach mine if anyone is interested -I am using ati driver as fglrx is worse than ati with this card ( surprising? nope ;) ) Performance is so-so (no games, fps ~550 as per glxgears).

---

### Post by transactionlogfiller on 2006-05-29
Ah, sorry - forgot that bit:

```

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

```

---

### Post by towsonu2003 on 2006-06-15
bumping

---

