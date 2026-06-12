---
title: "[HELP]Still the problems with refresh rate"
date: 2005-11-17
forum: General Help
---

### Post by c_coolguy on 2005-11-17
I'm using nVidia5700VE with SyncMaster795MB. The monitor can handle 1024*768@100Hz. But I can only use 1024*768@60Hz now. I wonder how can I persuade it work at 100Hz.
I've read several articals on this issue and rewrited corg.conf as following:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
	Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
EndSection

```

---

### Post by bin on 2005-11-17
Couple of thoughts

The first thing I notice is that the refresh rates shown for your monitor are roughly what you would expect to give 60 hz only. Have you checked the monitor manual to see what the _full_  range should be?

Once you've got that right it should work fine, but an extra option you may want to try once you've got the right refresh range is to give xorg your monitor dimensions

After VertRefresh put in a line:-
DisplaySize 285 210 use the actual width and height are in mm. of your screen.
Try this with the modeline # out so it isn't read.

in light

bin

---

### Post by bin on 2005-11-17
The next logical step will be to install the nvidia driver from the ubuntu repos.

The problem is that the final command that you run to enable the driver relies on your xorg.conf file NOT having been modified manually.

As far as I remember it's only a question of changing the line

Driver	"nv" to "nvidia" but you may want to check around the forum first

in light

bin

---

### Post by frodon on 2005-11-17
Modify your xorg.conf like that : > Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
[B]	HorizSync	30-85
	VertRefresh	50-160[/B]
EndSectionThen do a Ctrl+Alt+Backspace to restart the Xserver.

---

### Post by c_coolguy on 2005-11-17
I made it!
Thank both of you for your help:)
Actually I have tried to modify the xorg.conf before but only to cause an error when loading KDE. Perhaps I did something more:)
Anyway, I can fully enjoy Kubuntu now.
Thanks again.:KS

---

