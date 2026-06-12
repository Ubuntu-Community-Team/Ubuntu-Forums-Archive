---
title: "Toshiba Laptop Resolution Problem"
date: 2009-02-17
forum: Hardware
---

### Post by Diamond1984 on 2009-02-17
I've been working on this for a while and I have had no success.  Others have had similar problems and I've tried using their advice but nothing changes for me.  Ubuntu is not recognizing the graphics hardware (I think) and I can't set the resolution any higher than 800x600.  800x600 is the highest option available.  I've tried going in through the command line and modifying the necessary files and even when I save my changes nothing happens.  Any help would be greatly appreciated.

xorg conf file

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

 xrandr -q
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

 sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade XPAi1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 82
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm bus_master cap_list
       configuration: latency=8

---

