---
title: "force resolution and refresh rates AOC 9KLR-SLK"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by adonias on 2005-07-15
Hi all.

I'm trying to reach 1600x1200@75hz with my aoc monitor but i cant. In the monitor manual at the vendors page i have the following specifications:

HSync:  	30K ~ 95KHz
VSync: 	50 ~ 160Hz
Bandwidt:200 MHz (pixels/sec)
Max resolution: 	1600x1200 (75Hz)
Supported resolutions:
640x350@70Hz
720x400@70Hz
640x480@60/72/75/85Hz
800x600@60/72/75/85Hz
1024x768@60/70/75/85Hz
1280x1024@60/75/85Hz
1600x1200@60/65/70/75Hz

Here is my xorg.conf, but x never do more than 1280x1024@60Hz no matter what i change.

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"Coolbits" "1"
EndSection

Section "Monitor"
	Identifier	"AOC Spectrum"
	Option		"DPMS"
	HorizSync	30-95
	VertRefresh	50-160

	Modeline "1280x1024_85"  159.36  1280 1376 1512 1744  1024 1025 1028 1075  -HSync +Vsync
	Modeline "1280x1024_75"  138.54  1280 1368 1504 1728  1024 1025 1028 1069 -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"AOC Spectrum"
	DefaultDepth	16
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024_85" "1280x1024_75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



The output of ddcprobe is:

vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: NV34 Board - p162-2nz Chip Rev
memory: 131072kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 1 2
id: 770f
eisa: EPI770f
serial: 000dbe30
manufacture: 3 2004
input: sync on green, analog signal.
screensize: 32 24
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 640x480@60 Hz (VGA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
ctiming: 640x480@85
ctiming: 800x600@85
ctiming: 1024x768@85
ctiming: 1280x1024@60
dtiming: 1024x768@104
monitorname: AOC Spectrum
monitorname: 7E
monitorrange: 30-70, 50-130

I've reached 1600x1280@75hz with win xp but neede to check "Show all display modes for this device" in the advaced tab of display properties. 

I think that my vendor didn't recorded the ddc specs correctely. Is there a way to force my xorg.conf without linux validating it as i do with windows?

---

### Post by cLawhammer on 2005-07-16
You resolve the problem?
I have the same with a AOC  7KLR. Support 1024x768 at 100hz but i only can set up at 85hz.

Not the same, i can set up 1280x1024 at 85 hz, only have the problem at 1024.

---

### Post by adonias on 2005-07-16
no i dindn´t. I´ve even tryied to rename the ddcprobe and also i let only one 1280x1024 mode in xorg.conf @85Hz but every time i restart x it comes back in 60Hz... its very annoying.... i think that should exist an way to force the mode that i want... besides any safe procedure existent in x... like an expert mode or something like.... i´ve also ran the xorgcfg and xvidtune to try force higher refresh rates but somehow they all get constrained by the same results as reported by ddcprobe.
No clues... anyone can help?

---

### Post by cLawhammer on 2005-08-29
Info to add timmings modes to X.org. This works for me

[Kudos Kubuntu Faq](http://kudos.berlios.de/kf/kf1.html#misc)

---

### Post by adonias on 2005-08-29
I've added the time modes and it didn't worked. This is my xorg.log output:

(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 400 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 400 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(WW) NVIDIA(0): The user specified HorizSync "30.000-95.000" has been adjusted
(WW) NVIDIA(0):      to "30.000-70.000" (the intersection with EDID-specified
(WW) NVIDIA(0):      HorizSync "30.000-70.000")
(WW) NVIDIA(0): The user specified VertRefresh "50.000-160.000" has been
(WW) NVIDIA(0):      adjusted to "50.000-130.000" (the intersection with
(WW) NVIDIA(0):      EDID-specified VertRefresh "50.000-130.000"
(II) NVIDIA(0): AOC Spectrum: Using hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): AOC Spectrum: Using vrefresh range of 50.00-130.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz
(II) NVIDIA(0): Not using mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using mode "1600x1200" (hsync out of range)


It's discarding the modelines that i have specified because it says that the hsync is out of range compared with EDID-specified. Is there any way to force my HorizSync and VertRefresh? I know that it can damage my hardware... but these values i found in the monitor manual.

Regards.

---

### Post by cLawhammer on 2005-08-29
This is the xorg.conf that works for my 1024x768@100Hz.
It dont add any error line to xorg.conf, sorry i can't help you :(
1280x1024@85Hz and 1600x1200@75 is default in my monitor.

```

Section "Monitor"
	Identifier	"AOC Spectrum"
	HorizSync   30-95
	VertRefresh	50-160
	Option		"DPMS"
	#DisplaySize	338	270	# 1280x1024 96dpi
        DisplaySize 270 203              # 1024x768 96dp

        # 1024x768 @ 100Hz, 80.21 kHz hsync
        Modeline "1024x768"   115.5    1024 1056 1248 1440    768  771  781  802 -HSync -VSync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"AOC Spectrum"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
        Modes		       "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

``` 

I think as you, AOC don't configure right the ddc specs.

---

