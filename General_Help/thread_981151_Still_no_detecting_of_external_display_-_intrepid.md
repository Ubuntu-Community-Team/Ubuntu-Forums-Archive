---
title: "Still no detecting of external display - intrepid"
date: 2008-11-13
forum: General Help
---

### Post by maestrobwh1 on 2008-11-13
Aside from killing and restarting the x-server, is there any tweak I can use have an external monitor/projector be recognized?  I was hoping with intrepid that I would be able to plug in a projector and just be able to configure it from system settings.  Even at the command line, 

$ xrandr -q 

Only brings up my internal display, even with the projector attached and working.  I find this odd. Adding other items to my xorg doesn't seem to make a difference (For example: Option "monitor-VGA" "VGA" under devices and making a separate reference to it as device/monitor).  Not sure if I have to add a virtual section, but being that the xorg.conf is becoming very basic (thankful overall for this), I am not sure if anything put there is even taken into account.  Intrepid configured my xorg as follows, with the projector attached and working.

**sudo dpkg-reconfigure -phigh xserver-xorg **

results in:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Previously with my manual tweaks

Section "Device"
	Identifier	"Configured Video Device"
[B]     Option 		"Monitor-VGA" 	"VGA"
	Option		"Monitor-LVCD" 	"LVCD"[/B]
EndSection

Section "Monitor"
**	Identifier	"LVCD"**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

So do I need to add a "virtual section" and two references to screens?

---

