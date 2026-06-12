---
title: "All resolutions not available in Nvidia Settings  (even with correct EDID)"
date: 2009-11-20
forum: Hardware
---

### Post by rage007 on 2009-11-20
Howdy.

I have an **Nvidia FX5500** 256mb card running **Ubuntu Karmic Koala 9.10** with the stock **nvidia-glx-173** drivers installed.  I have it hooked up via DVI cable to a **Princeton VL2418W** 24" LCD Flat panel, which should have a max resolution of 1920x1200.

Many battles have been fought over getting this setup to display higher than 1600x1200.  That is the top resolution available in Nvidia Settings.  I have tried using xrandr to calculate manual Mode Lines, many many MANY different settings in my xorg.conf, and looked in the bottom of a dozen Cracker Jacks boxes for any kind of answer that would help.

In the above metaphor "Cracker Jacks Boxes" are the first 30 pages of google results for any combination of keywords like nvidia settings resolution driver 1920x1200 add modeline xrandr etc etc etc.

I tried disabling all EDID information and specifying manual options, which did not work.  So I dumped and parsed my EDID binary which very surprisingly shows that the monitor indeed should be showing 1920x1200.  I tried confirming the option in my xorg.conf with 'Option "UseEDID" "TRUE" even though it is true by default.

EDID value:
```

parse-edid: parse-edid version 2.0.0
parse-edid: EDID checksum passed.

	# EDID version 1 revision 3
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "VL2418W"
	VendorName "NUI"
	ModelName "VL2418W"
	# Block type: 2:0 3:fd
	HorizSync 31-81
	VertRefresh 56-75
	# Max dot clock (video bandwidth) 160 MHz
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
	# DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

	Mode 	"1920x1200"	# vfreq 59.950Hz, hfreq 74.038kHz
		DotClock	154.000000
		HTimings	1920 1968 2000 2080
		VTimings	1200 1203 1209 1235
		Flags	"-HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	# Block type: 2:0 3:ff
EndSection

```


I am not sure how to continue troubleshooting this issue.  I have wiped and regenerated my xorg.conf several times with dpkg and removed/reinstalled the nvidia drivers a few times for good measure.  

I have attached the specs for the monitor and my current xorg.conf in case that information is useful.

Any help would be appreciated.  I hate losing arguments with technology.

---

### Post by yanaek on 2009-11-30
EDIT:
sorry, not a bug, just a limitation of the GeForce FX series:
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)
> 
DVI support for compatibility with nextgeneration flat panel displays with resolutions up to and including 1600×1200


but strange thing, this option in Screen section helps ;)
> 
Option "ModeValidation" "NoMaxPClkCheck"

with small "L" letter in PClk

---

