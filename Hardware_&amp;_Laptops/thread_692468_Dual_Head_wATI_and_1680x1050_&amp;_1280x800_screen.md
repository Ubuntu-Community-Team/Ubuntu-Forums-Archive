---
title: "Dual Head w/ATI and 1680x1050 &amp; 1280x800 screens"
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by poe9514 on 2008-02-09
I have a laptop with a 1280x800 screen, and an external monitor at 1680x1050.  I'm running Gutsy Gibbon 7.10.  ATI Mobility Radeon 9700 graphics card.  I run Compiz, also.

Some useful specs on my system:
```

poe9514@perickson:~$ Xorg -version

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux perickson 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686
Build Date: 18 January 2008
```

I only switched to Ubuntu from Windows about a month ago, but I haven't been happy with dual screen support.  What I WANT to setup, ideally, is:

[LIST]
[*] dual screen support (dual head) from my monitor and laptop screen
[*] when dual screened, I'm fine with separate X servers, but I'd prefer to have only a single workspace on the laptop screen, and my regular workspaces and Compiz on the external monitor (basically, a separate X server on the laptop screen running Metacity would work)
[*] Keeping Compiz is important to me
[*] MOST IMPORTANTLY, I need the ability to easily switch to just the laptop screen to go mobile
[/LIST]

I have a script setup to switch between using either the laptop screen or the monitor using xrandr, and that's worked for my mobile needs:

```

#!/bin/bash
xrandr --auto
sleep 0.5s
if [ "$1" = "screen" ]; then
        xrandr --output LVDS --off
else
        xrandr --output VGA-0 --off
fi
```

Here's the relevant portion of my xorg.conf as it stands right now:

```

Section "Device"
	Identifier	"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
        Option          "GARTSize" "128"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Any suggestions as to how to achieve this would be greatly appreciated!

Thanks in advance!

---

