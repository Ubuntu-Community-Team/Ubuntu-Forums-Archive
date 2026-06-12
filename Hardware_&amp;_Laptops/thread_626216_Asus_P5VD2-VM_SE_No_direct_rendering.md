---
title: "Asus P5VD2-VM SE No direct rendering"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by troubleman on 2007-11-28
Hi, 

I have an Asus P5VD2-VM SE motherboard, with some kind of integrated graphics card (intel I assume). I've installed Gutsy on it and I can't get direct rendering to work. 

Here is my xorg.conf file ( minus the stuff about input devices): 

```
Section "Files"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
#	Driver		"i810"
	BusID		"PCI:1:0:0"
	Option "CacheLines" "3582"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
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
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

I tried older distributions, but none of them could find my SATA hard drive. The vesa driver is working (with my crappy old CRT monitor but without hardware accelerated graphics). I've tried using the graphics configuration tool to switch to other drivers, but the screen just goes blank and switches back to the vesa driver. Any advice would be greatly appreciated.

---

### Post by troubleman on 2007-11-29
bump

---

### Post by troubleman on 2007-11-30
Bump Bump

---

### Post by troubleman on 2007-12-01
Bump? :(

---

### Post by troubleman on 2007-12-04
Bump...:confused:

---

### Post by useResa on 2007-12-04
I noticed that you are getting little response on this.
Sorry about that .. maybe no one knows the answer?

All I can tell is that you are currently using the "vesa" driver, which AFAIK will never get you direct rendering. However, I unfortunately do not know enough about this subject to advise you on which driver may work.

Surely hope that someone will help you out soon.

---

### Post by troubleman on 2007-12-04
Thanks useResa! I'll keep tinkering and see what I can figure out. 

-tm

---

### Post by useResa on 2007-12-05
I have done some additional searching to see if I could find something.
Doing so I came across [this thread]("http://ubuntuforums.org/showthread.php?t=485646") (**HOW TO: Compiling and Installing the OpenChrome Graphical VIA Driver**).
Maybe this could be a solution for you, however -- a small warning in advance ;) -- [this post]("http://ubuntuforums.org/showpost.php?p=3726969&postcount=87") indicates that it might not work.
However, I did not read the entire thread to see if it got fixed.

Maybe you could post your question in the indicated thread to see what comes back?

---

### Post by jdalegonzalez on 2008-01-17
That motherboard has a VIA Chipset P4M900 integrated graphics card on it.  As far as direct rendering goes, it's my understanding that the drm code distributed with the gutsy kernel (2.6.22) and older don't recognize the P4M900 chipset.  On the openchrome site, there is a kernel patch that adds support for both DRM and AGPGART - 
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=P4M900]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=P4M900") . 

However...

1) It does require that you patch your kernel.  Here is the page describing how to do it [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile").  Make sure you read the big hairy warning before you decide to try it.

2) I've gotten the DRM and AGPGART patched in but haven't been able to get the openchrome driver to work  YMMV.

---

### Post by troubleman on 2008-01-17
Thank you very much. I had all but given up on it. I'm not at that machine but I'll give it a try.

---

