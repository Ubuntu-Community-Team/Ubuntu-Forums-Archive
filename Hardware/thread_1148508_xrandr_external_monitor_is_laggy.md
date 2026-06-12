---
title: "xrandr external monitor is laggy"
date: 2009-05-04
forum: Hardware
---

### Post by scales on 2009-05-04
Hi all,
I have successfully gotten my eee 1000he laptop working with an external monitor via xrandr.  I have noticed however that windows and content on the external monitor are laggy.  example, scrolling in a website is terrible.  I have checked the refresh rate on the monitor, and that is fine at 75.0.  I will also post my xorg.conf file.  here is the command i use to get the external display working:
> [SIZE="1"]xrandr --output LVDS --auto --left-of VGA --auto[/SIZE]

alone the external monitor works fine, but when i do the dual setup it has problems.  i am wondering if it is xrandr and the driver?  thoughts?

here is my xorg.conf:

> [SIZE="1"]Section "Device"
    Identifier    "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
    Driver        "intel"
    BusID        "PCI:0:2:0"
EndSection


Section "Monitor"
	Identifier	"laptop-display"
EndSection

Section "Monitor"
        Identifier      "ext-monitor"
        Option          "DPMS"
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Monitor		"laptop-display"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	DefaultDepth	24	
	SubSection "Display"
		Virtual         2464 900
	EndSubsection
EndSection

Section "Screen"
        Identifier      "External Screen"
	Monitor         "ext-monitor"        
	Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Virtual         2464 900
                Modes           "1440x900"
        EndSubSection
EndSection


Section "ServerFlags"
	Option "DontZap" "Off"
EndSection[/SIZE]

---

