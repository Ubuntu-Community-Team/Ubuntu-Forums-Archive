---
title: "Concerns about overheating with the nvidia driver"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by norfenstein on 2005-04-27
I recently did a full reinstall, mostly to fix the nvidia drivers that were broken upgrading from Warty to Hoary. Everything actually works correctly but when I start X using the nvidia driver the fan on my video card (GeForce FX 5900XT) revs up to full speed and makes a loud and disconcerting noise. I have a small case so I've always been paranoid about overheating, but is this something I should worry about? I left it on all day yesterday and nothing melted down, but that's not exactly something I want to risk by ignoring it. This didn't happen in Warty and doesn't happen when using the nv driver. Also it requires a full reboot to calm down, just quitting X won't stop it. Here're the relevant parts of my xorg.conf:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NvAGP" "2"
	Option		"RenderAccel" "true"
	Option		"NoLogo" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
If anyone can help with this I'd be very grateful.  :-?

---

### Post by norfenstein on 2005-04-29
I hate to bump my own thread, but does no one know anything about this? If I don't get any responses I'll let the thread die and just, uh, never use my video card again. :(

---

### Post by nad on 2005-04-29
Have you read the nvidia docs on your computer to see if this is an issue with your driver? The forums at nvidia?

Have you tried uninstalling and reinstalling the nvidia-glx package? How about a different resolution? Is the gpu overheating, fan or cooling path obstructed?

---

### Post by norfenstein on 2005-04-29
Changing resolutions and reinstalling the nvidia-glx package had no effect. I found nothing useful in the documents installed with the driver and tried different combinations of options with no effect. I can't imagine this is a physical problem as nothing inside my case has changed since I installed the card and the nvidia drivers gave me no problems under Warty. Is there some way of measuring the temperature of the GPU? I'll look further into the nvidia support forums, thanks for your reply in any case.

---

### Post by FerGeCo on 2006-06-14
it's a bit late but you could try nvclock -i (sudo apt-get install nvclock).  or else try lm-sensors ([http://ubuntuforums.org/showthread.php?t=2780&highlight=temperature](http://ubuntuforums.org/showthread.php?t=2780&highlight=temperature))

---

### Post by norfenstein on 2006-06-15
I've tried nvclock (the version in breezy didn't support my card and the version in dapper segfaults when using the nvidia driver) but unfortunately being able to manually change the fan speed won't be quite enough. Since starting this thread I've managed to find references to other people having the same problem (some of whom have reported newer drivers fixing it for their cards) so hopefully it will eventually get fixed by nVidia. Thank you for replying regardless.

---

