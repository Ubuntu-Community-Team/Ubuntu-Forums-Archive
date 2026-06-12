---
title: "Adjusting display resolution"
date: 2009-11-07
forum: Hardware
---

### Post by NaCl on 2009-11-07
I have this Toshiba Satelite A205 laptop with Intel GMA X3100 and 15.4" widescreen that appears to malfunction at incorrect resolution. When it had Vista, it would load into Windows, go blank, and then freeze. I know it freezes because the cap lock light would not turn on.
I was able to load and install ubuntu 9.04 under safe mode. After installation, I was able to boot into ubuntu in 1024x768 @ 61 Hz. I upgraded the distro and it no longer boots at 1024x768 @ 61 Hz. I tried adding

    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_61.00"
    EndSubSection
EndSection

to xorg.conf, but no luck. 
It displays:
Starting up...
Undefined video mode number: 400
Press <ENTER> to see video mode available,
displays a list of modes.

I have tried so far:
1024x768x16 VESA
1024x768x32 VESA.
I would hear the startup sound for both, but no blank (or very distorted screen - I'd see 2~4 distorted shells).

I am thinking about reinstalling 9.10 in safe mode. Just need a working computer to do some word processing and web browsing until Black Friday comes.

Here is original xorg.conf reading
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Thanks in advance.

---

