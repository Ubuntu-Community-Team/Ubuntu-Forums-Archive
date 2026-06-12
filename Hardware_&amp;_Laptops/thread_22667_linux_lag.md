---
title: "linux lag"
date: 2005-03-29
forum: Hardware &amp; Laptops
---

### Post by mrbright on 2005-03-29
Ever since ive installed hoary 5.04 ive been noticeing a slight lag on my laptop. So i decided to look at my system monitor. One thing i noticed was that my CPU resorces are allways between 20 and 50%. If i move a window around  it spikes to 100. Now im really new at this whole linux thing (infact the reason im here is because of ubuntu and a very patient friend). Im not exactly sure what to blame this problem on so Ill just go with something is wrong with my graphics drivers for my onboard gpu.

My friend told me to post this section of my xorg.config  so  here it is

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"

He allso told me to post a section of my glxgears  so here it is

1573 frames in 5.0 seconds = 314.600 FPS
2846 frames in 5.0 seconds = 569.200 FPS
1623 frames in 5.0 seconds = 324.600 FPS
1709 frames in 5.0 seconds = 341.800 FPS
1663 frames in 5.0 seconds = 332.600 FPS
1681 frames in 5.0 seconds = 336.200 FPS
1591 frames in 5.0 seconds = 318.200 FPS
1269 frames in 5.0 seconds = 253.800 FPS
443 frames in 5.0 seconds = 88.600 FPS
597 frames in 5.0 seconds = 119.400 FPS
1659 frames in 5.0 seconds = 331.800 FPS
1657 frames in 5.0 seconds = 331.400 FPS


Some one please help I really like this OS Its just laggy, real laggy

---

### Post by Whiffle on 2005-03-29
Open up a terminal and run "top".  Then look at teh %CPU column and make sure nothing is stealing your cpu.  

I'm not sure which drivers go with that graphics hardware...

---

### Post by askreet on 2005-03-29
[QUOTE=mrbright]Ever since ive installed hoary 5.04 ive been noticeing a slight lag on my laptop. So i decided to look at my system monitor. One thing i noticed was that my CPU resorces are allways between 20 and 50%. If i move a window around  it spikes to 100. Now im really new at this whole linux thing (infact the reason im here is because of ubuntu and a very patient friend). Im not exactly sure what to blame this problem on so Ill just go with something is wrong with my graphics drivers for my onboard gpu.

My friend told me to post this section of my xorg.config  so  here it is

Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"

He allso told me to post a section of my glxgears  so here it is

1573 frames in 5.0 seconds = 314.600 FPS
2846 frames in 5.0 seconds = 569.200 FPS
1623 frames in 5.0 seconds = 324.600 FPS
1709 frames in 5.0 seconds = 341.800 FPS
1663 frames in 5.0 seconds = 332.600 FPS
1681 frames in 5.0 seconds = 336.200 FPS
1591 frames in 5.0 seconds = 318.200 FPS
1269 frames in 5.0 seconds = 253.800 FPS
443 frames in 5.0 seconds = 88.600 FPS
597 frames in 5.0 seconds = 119.400 FPS
1659 frames in 5.0 seconds = 331.800 FPS
1657 frames in 5.0 seconds = 331.400 FPS


Some one please help I really like this OS Its just laggy, real laggy[/QUOTE]
 You may want to do all your updates in synaptic to make sure it's not a bug thats already been fixed :D I've had that problem before.

Hopefully thats all it is.

Best of Luck,
 Skreet

---

### Post by mrbright on 2005-03-29
I just updated everything and the problem was helped a lot. Its still there when I move a window around a lot (especially over firefox) but thats about it. i ran top  and the xorg was takeing up about 5% but not anything out of the ordinary I think. It seems that there is a another thread that has a similar problem so me thinks its a bug. :neutral: thanks for the reply

---

### Post by askreet on 2005-04-02
If you have a 3d accelerated video card nvidia or ati you will want to install the drivers, as it makes a huge difference even in desktop performance.

Maybe that'll finish off that issue? :D

-askreet

---

