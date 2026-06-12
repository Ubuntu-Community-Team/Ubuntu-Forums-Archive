---
title: "How can I make bigger Hz s-video out on X3100 graphics?"
date: 2009-04-09
forum: Hardware
---

### Post by Femaq on 2009-04-09
Hello, I have been trying to make my acer 5920 with GMA X3100 display TV through S-video.
Finally I found solution with settings in xorg.conf:

Section "Monitor"
Identifier "VGA"
Option "Ignore" "true"
EndSection

Section "Monitor"
Identifier "LVCD"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "TV"
Option "Ignore" "false"
Option "TV_FORMAT" "PAL"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 800
	EndSubSection
EndSection

Section "Device"
Identifier "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
Driver "intel"
BusID "PCI:0:2:0"
Option "monitor-VGA" "VGA"
Option "monitor-TV" "TV"
Option "monitor-LVCD" "LVCD"
EndSection


However, the refresh rate to TV is **25Hz** while my TV supports 100hz...and I have few output resolution options to select. 
Is there anything wrong I wrote in xorg.conf?
What can I do to make refresh rate and resolution higher?

---

