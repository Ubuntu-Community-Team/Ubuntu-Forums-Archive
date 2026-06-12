---
title: "Display problems on Acer Aspire 5003WLMF"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by sgenier on 2006-08-08
Hello,

I recently installed Ubuntu 6.06 on my Acer Aspire 5003WLMF. I had no problem with the instalation but, as soon as I started Ubuntu, I noticed that the display was strange. Some horizontal lines were slightly misaligned and the image looked stretched. I first thought there was a problem with X.org, so I logged in text mode to play with the config file. However, the bottom part of the console (about 6 lines) were truncated. Does anyone have a clue about what is going on ?

The graphic adapter is a mirage 2 (SiS M760GX).

Thank you.

---

### Post by pdub on 2006-08-08
What is the native resolution of the screen?

Have you modified your /etc/X11/xorg.conf file to reflect the proper resolutions and horizontal / vertical frequencies?

My Dell 820 has a 1680x1050 resolution and my xorg.conf setting are:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-84
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" 
	EndSubSection
```

As for the resolution in the console have a look at this thread.

[http://www.ubuntuforums.org/showthread.php?t=215566](http://www.ubuntuforums.org/showthread.php?t=215566)

I had to change the defoptions when I used SUSE.

---

### Post by sgenier on 2006-08-09
I tried to pass vga=3840 at boot time. This fixes the truncated console, but it now gives me an error message just after the kernel is loaded and boot messages are made in tty1 without the Ubuntu logo and the coloured text.

Here is a part of my xorg.conf :
```

Section "Monitor"
	Identifier	"Generic LCD"
	Option		"DPMS"
	HorizSync	30-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic LCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I added the "1280x800" resolution and tweaked the refresh rates. I am not 100% sure about these rates. Can I damage my monitor with incorrect rates?

It refuses to display the correct resolution, but the screen stopped flickering. There is still the misalignement problem.

Here is part of Xorg.0.log:
```

(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 661/741/760/761 PCI/AGP VGA Display Adapter rev 0, Mem @ 0xe8000000/27, 0xe2100000/17, I/O @ 0xa000/7

[...]

(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: SiS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) VESA(0): VESA VBE OEM Product: 6330
(II) VESA(0): VESA VBE OEM Product Rev: 2.27.g8

[...]

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Generic LCD: Using hsync range of 30.00-60.00 kHz
(II) VESA(0): Generic LCD: Using vrefresh range of 50.00-75.00 Hz
(II) VESA(0): Not using mode "1280x800" (no mode of this name)
(II) VESA(0): Not using built-in mode "1280x768" (width too large for virtual size)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (75, 75)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (117)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)

```

Note that under Windows the 1280x800 works and is the default, with a 32bit coulour depth

---

### Post by pdub on 2006-08-10
Are you running the SiS video drivers?

---

### Post by sgenier on 2006-08-10
According to the log, it seems to be recognized and handled by a generic driver. My chip, M760GX, does not seem to be listed anyway ([http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm))

I have tried to add a modeline for 1280x800, but kept saying that there was no mode of this name.

---

