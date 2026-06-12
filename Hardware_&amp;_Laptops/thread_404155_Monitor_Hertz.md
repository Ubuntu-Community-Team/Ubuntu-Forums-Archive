---
title: "Monitor Hertz"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by Outlaw on 2007-04-08
Is there a way to have native full screen games run at a refresh rate higher than 85 in ubuntu? For instance, my desktop is 1280x1024@85hz, but I would like to be able to run Quake 3 in 800x600@120hz. Thanks :)

---

### Post by Wim Sturkenboom on 2007-04-08
Not sure, but please post sections device, monitor and screen from /etc/X11/xorg.conf.

PS and please post the make and model of videocard and monitor

---

### Post by hardyn on 2007-04-08
most new flat panels run best at 60hz... or only at 60hz... if you have a super high quality old CRT... then you might get some additional image stability using 120hz... but sync rate doesn't do anything for performance of the system.

---

### Post by Outlaw on 2007-04-08
Section "Device"
	Identifier	"ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)]"
	Driver		"ati"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL P1130"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R423 UI [Radeon X800PRO (PCIE)]"
	Monitor		"DELL P1130"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


I play Quake 3 pretty competitively (have won various prizes/money and the works). Almost everyone who plays Q3 competitively uses 120hz, it helps alot.

---

### Post by hardyn on 2007-04-08
well you can add VertRefresh x.x - 120.0
to the monitor section... but monitor refresh is not a performance thing.

if your monitor is only capable of 60-75 hz as most are... 120 will do nothing but DESTROY YOUR MONITOR.

i good monitor will trap the overscan, and not allow the monitor to start.  If you are using a flat pannel, refresh means much less than it did with a CRT as the screen are repainted differently.

good luck.

---

### Post by Outlaw on 2007-04-08
"If your monitor is only capable of 60-75 hz as most are... 120 will do nothing but DESTROY YOUR MONITOR."

Haha, my 22" CRT is capable of 160hz at the resolution in which I want to use 120hz.

I also think you misunderstand my dilemma. In 1280x1024 my highest refresh rate is 100. In 800x600 my highest refresh rate is 160. I use 1280x1024@85hz on my desktop. What I am asking is if there is a way that **when i run full screen games at lower resolutions** such as 800x600 if there is a way to have the refresh rate go up. Quake 3 is normally capped at 125fps, and anything below 120hz hurts my eyes.

---

### Post by daldinit on 2007-04-08
Yeah, I know what you mean, there used to be tools for that in Windows XP, before drivers included such a feature. (because before that happened games using hardware acceleration reverted back to 60Hz in Windows XP) I don't know about Ubuntu though. I don't know if refreshrates remain the same for desktop and 3D accelerated modes. When you set your desktop to 800x600 on 120Hz, and lauch the game...do you keep that refreshrate (i bet you can tell by just looking at it)?
If yes, consider that as a cheap workaround.

Anyways, I kind of hate to mention this but... I -think- that you would get better performance in Windows for most games anyway...which probably matters, because I've read a loooong time ago about being able to jump higher in Q3 when reaching a higher fps or something like that. :)

---

### Post by Outlaw on 2007-04-08
I see, the game runs fine in ubuntu, fps is of no issue...theoretically without capped fps I could reach over 1000fps, but it does not matter as fps is capped at 125 nowadays inside of Q3

---

### Post by Outlaw on 2007-04-09
ttt

---

### Post by Outlaw on 2007-11-24
Was wondering if anyone knew of a solution, as I still deal with this problem? (Same Hardware)

---

### Post by Outlaw on 2007-11-24
:(

---

