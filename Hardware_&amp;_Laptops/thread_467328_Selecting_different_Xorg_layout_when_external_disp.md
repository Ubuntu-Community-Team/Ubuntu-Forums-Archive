---
title: "Selecting different Xorg layout when external disp is connected?"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by Master Ar2ro on 2007-06-07
I have an Aristo Slim 430 laptop and Belinea 101901 LCD. I managed to make X see the LCD and use it's full resolution, but it still requires to restart X whenever I want to change from/to the laptop screen plus if I make the external LCD my default screen and boot the laptop without it, then I'm getting a blank screen on the laptop and nothing else.
Is there a way to make the X server determine whether the LCD is connected at boot, and choose the appropriate layout? Or perhaps there's a way, to make X switch the screen during runtime?

I configured the external screen in the following way (part of xorg.conf):
```
...
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	Option		"MonitorLayout" "CRT,NONE"
#	Option		"Clone" "True"
	Option		"DDCMode" "True"
	Option		"DevicePresence" "True"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
#	HorizSync	28-64
#	VertRefresh	43-60
	DisplaySize	376 301
	HorizSync	31-83
	VertRefresh	56-75
EndSection

```
When I change *Option "MonitorLayout" "CRT,NONE"* to *"CRT,LFP"* or *"LFP,CRT"* the only screen working is the one on the laptop and the LCD is not used. As far as the runtime switching screens is concerned, I did run into information about the i810switch program, however it's not in the feisty repositories.

Can anyone help?

---

