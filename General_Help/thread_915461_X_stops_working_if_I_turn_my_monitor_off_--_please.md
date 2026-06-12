---
title: "X stops working if I turn my monitor off -- please help!"
date: 2008-09-09
forum: General Help
---

### Post by dagoss on 2008-09-09
I'm at my wits end with this.  I've done countless Google searches and wasted so many hours trying to figure out what the hell is wrong, but with no luck.  This is trying me up the wall.

I recently purchased a new monitor (Acer AL2216Wbd).  I'm using the dvi input and it is working fine, except when I turn off the monitor then try to turn it back on, it claims to be getting no signal.  The only thing I can do is ctrl+alt+backspace to restart X, at which point the screen comes back.  Obviously this is unbelievably frustrating.

I have a Radeon 9600 XT.  I'm using the fglrx driver.  I tried the free drivers (and they let me turn my monitor back on), but the ran so badly for me that they were essentially unusable.  Here is my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option "MonitorLayout" "TMDS, TMDS"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Here is lspci:

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
```

And, if you know what is wrong, here is my undying gratitude:
```
$ echo $HELPME
This is driving me insane!  I beg you -- !

```

---

