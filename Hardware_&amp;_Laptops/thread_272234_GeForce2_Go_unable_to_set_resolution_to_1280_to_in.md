---
title: "GeForce2 Go unable to set resolution to 1280 to interface with LCD flat screen displa"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by skyemoor on 2006-10-05
Dell Latitude C810
GeForce2 Go
Dell 1907FPc flat screen display
Dapper 6.06

Background: Ubuntu works fine on my laptop display, though only allows 1600x1400 resolution.

Problem: My flat screen display can only show 1280x1024, so that's what I set my resolution to. The laptop image shrinks, instead of shows at lower resolution. When I hook up my flat screen display, it gives the error:

"1. Analog input. 1280x1024 60 Hz resolution optimal"
Oddly enough, Ubuntu startup displays show up, all the way up to showing gnome (I'm assuming).

I tried;
  [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
  Result: Had to restore my x11.conf file

Looked at other help pages, but the only one I saw had a list of legacy GeForce2 display adapters, though none were mine, so I couldn't tell if I should use the xgl or legacy driver.

Here's a smattering of my xorg.conf;

  Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	16


How can set the resolution correctly so that I can use my 1280x1024 monitor?

---

### Post by skyemoor on 2006-10-05
Here are more details from my now modified xorg.conf;

SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1600x1200"
	EndSubSection

Originally, only 1600x1200 was listed.  I added 1280x1024 as shown above, but now when the display resolves to gnome, the window I can see things in is slightly smaller than full size, and I have to reduce my screen resolution to 1280x1024 in order to see the outer edges of the windows (it's like looking at a picture where the borders cover up the outer edge).

---

### Post by skyemoor on 2006-10-06
... and now my mouse is moving around the screen erratically and I can't use it to select anything.  Are there hotkeys to get out of gdm?

---

### Post by AdventHorizon on 2006-12-10
I'm having the same resolution problem...Has anyone managed to figure it out?

---

