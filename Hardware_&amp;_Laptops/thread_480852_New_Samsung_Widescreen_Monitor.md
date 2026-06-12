---
title: "New Samsung Widescreen Monitor"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by inferno34 on 2007-06-21
So my Old monitor just broke so I had to get a new one a samsung SyncMaster 906BW and I have a ATI Radeon 9950 , now this monitor supports 1440x900 and I got it going at the resolution, now the only problem is that the text is a tad small..(probably the display seize) and I dont see the Bottom Bar, if I take a Screen shot it shows up fine, but I can't see the Bottom bars, if I open Firefox, the "Done" at the bottom of the browser bar is cut off abit, just the lower parts) and the rest below that I can't see. I tried looking at the forums and I did not find anything, can anyone help me? Also I tried the modeline and it was still doing the same thing) 
> 

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
	DisplaySize 381 238
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection



---

### Post by inferno34 on 2007-06-21
Well, seems like I fixed it. With the help of someone I know :)

I was missing the ATI drivers

I used 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) 

To help me install the drivers and everything looks fine now time to enjoy it :popcorn:

---

### Post by racso39 on 2007-06-21
I wonder if using Envy would work.

---

