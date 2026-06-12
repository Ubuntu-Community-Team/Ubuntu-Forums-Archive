---
title: "Scrambled screen"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by OzBoy on 2005-05-20
I have just installed the AMD64 5.04 on a brand new machine.  It installed without any errors and boots up fine.  When it starts X, the screen is completely scrambled - it looks like when you have the refresh rate set too high.  I booted into recovery mode and tried changing the settings in /etc/X11/xorg.conf as suggested in the forums without success.  Can anybody lend a hand?

---

### Post by JaF on 2005-05-20
[QUOTE=OzBoy]I have just installed the AMD64 5.04 on a brand new machine.  It installed without any errors and boots up fine.  When it starts X, the screen is completely scrambled - it looks like when you have the refresh rate set too high.  I booted into recovery mode and tried changing the settings in /etc/X11/xorg.conf as suggested in the forums without success.  Can anybody lend a hand?[/QUOTE]
Does it look like this?
[IMG]http://www.joefarish.co.uk/images/res/1280.jpg[/IMG]
If it is then you and I are having the same problem. I have started a thread at: [http://ubuntuforums.org/showthread.php?t=35785](http://ubuntuforums.org/showthread.php?t=35785)

---

### Post by OzBoy on 2005-05-20
Oh, no.   Yours seems to resemble text.  I have attached a shot of my screen.
As you can see (vaguely), my cursor is perfect and the rest of the screen is absolutely, 100%, true-blue, gold-plated, stoned motherless unreadable.

This was a clean install of Ubuntu 5.04 on a brand new computer with a brand new hard drive with an old, fuzzy brain doing the install.  I went for the default options where they were presented, rebooted at the appropriate times, and the result as above is the login screen.

My xorg.conf:

Section "Device"
        Identifier	"ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-81
	VertRefresh	56-76
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
#	Modeline	"1248x936@75" 135.00 1248 1280 1792 1824 936 953 965 983
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

The monitor is a 17" flat panel (Benq FP71E), native is 1280*1024 at 80Hz.  I have tried commenting out the Modeline section (as above), installing a new modeline (the second modeline in the code above) and changing the DefaultDepth to 16, all of which were suggested in the forums.

Hope you can help...

---

### Post by zaguar on 2005-06-19
I've got a 9250, and the GDM is scrambled, completely screwed, like the refresh rate is too high.  i got a 1024x768 monitor.

---

