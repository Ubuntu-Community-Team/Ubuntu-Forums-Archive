---
title: "Turn off lcd monitor"
date: 2006-10-29
forum: Hardware &amp; Laptops
---

### Post by esaym on 2006-10-29
It seems like every time I reboot, it changes the time suspend time for my lcd monitor.  I keep it set at 5 minutes and mysteriously it keeps changing back to the default 30 minutes or sometimes disabled completely.  Also I noticed when the lcd does suspend, the backlight will stay on for another 10 minutes or so and then it will turn all the way off. 

xorg.config has a funny entry if you ask me:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
```

as you can see the monitor is using dpms while the screen is using "default screen".  Is that right?  Also if I close the laptop lid it will shut the screen off but I will never be able to get it back on again and have to force the computer to restart.

Anyone ever have any of these problems before?

---

### Post by kerry_s on 2006-10-29
I use a script to make sure my settings are set the way i want, i also turned it into a launcher to turn the screen off in 5 seconds instead of 5 minutes, that way i have a choose i can let it turn off by it self in 5 min. or 5 sec's. I did this because mplayer likes to disable dpms when it runs.

---

### Post by esaym on 2006-10-29
oh, hmm.  Interesting.  Thanks though.

---

### Post by esaym on 2006-11-03
> **esaym said:**
> It seems like every time I reboot, it changes the time suspend time for my lcd monitor.  I keep it set at 5 minutes and mysteriously it keeps changing back to the default 30 minutes or sometimes disabled completely. 


still having the same problem.  Does anyone know off hand where the config file for the monitor settings is for kde?  Also I know there is a way to do with with the xorg.conf, anyone know?


[IMG]http://la.gg/upl/snapshot3.png[/IMG]

---

### Post by esaym on 2006-11-04
ok I have gotten somewhere.  

adding:

```
Option "OffTime"	"10"	# Turn off (DPMS)
```

under Section "ServerLayout" turns off the lcd after 10 minutes.  The number in the picture I posted above also changed to 10 so I guess it was directly reading the xorg.config yet was unable to write to it since I have edited it beforehand.

Also to get the backlight to work right I had to make sure I had use dpms in my monitor section and also in my video card section since I use nvidia:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 Go]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "DPMS" "TRUE"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection
```

:mrgreen:

---

