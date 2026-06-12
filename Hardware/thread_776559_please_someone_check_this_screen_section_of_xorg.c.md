---
title: "please someone check this screen section of xorg.conf"
date: 2008-04-30
forum: Hardware
---

### Post by maestrobwh1 on 2008-04-30
I want to configure an external monitor for my asus eee-pc (kubuntu 7.10).  It has a display of 800x480.  My external monitor has a maximum resolution of 1280x1024.  If I just plug it in, it does work but there are some quirks.  First, notifications that ought be in the tray pop up about mid way up the external screen in kde3.  It also happens running kde4 but also, the panel appears midway up the screen and about 3/4's over it ends.  I can set it to appear at the top and that sort of makes it usable.  

Parts of things are mimicking the 800X480 so using some posts off of the net, I modified my xorg.conf and saved it as a different name for now. ** Do the modifications of this section (below) create a scenario where when the external monitor is plugged in, the resolution of 1280x1024 will occur, and the eee-pc display will just show part of the screen?**

I tried using systemsettings and xrandrtray, but those both made a total mess and either kept kdm from loading, or brought me to an unusable low resolution screen.

**With the external monitor plugged in, I don't care what appears on the laptop display.**



Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller Two"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
                Depth           24       
		Virtual 	2080x1504   **_ "I assume this part is needed and I just added my resolutions together"_**
                Modes           "800x480" "1280x1024"
        EndSubSection
EndSection

Section "Screen"
	Identifier	"External Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller Two"
	Monitor		"External Monitor"
	DefaultDepth	24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
       	Option          "MergedFB" "true"
        Option          "MetaModes" "800x480 800x480-1280x1024"
        Option          "MergedDPI" "100 100"
        Option          "CRT2Position" "LeftOf"
EndSection

---

