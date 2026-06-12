---
title: "Gutsy with a Samsung SyncMaster 920NW resolution issues"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Garrulousbrevity on 2007-10-20
Hey, so I just got to installing Gutsy today, and I can't get the resolution quite right.  The computer doesn't seem to have much of an issue recognizing the native resolution (1440x900), and the xorg.conf files still seems to be properly configured for it, however, I now have a large black bar on the left side of my screen.  For any lower resolution the bar is gone.  I see that other people have had similar problems, but I'm not seeing anyone with a fix that works for me. 

I have an ATI Radeon 9000 graphics card. 

I've tried rewriting my xorg.conf file several times, and every time the correct resolution is recognized, I get the black bar on the left side of the screen.  At first I kept my old xorg.conf from Fesity. 

Currently, after using the Gutsy automated thingy for monitors, and adjusting it to actually have 1440x900 resolution, it reads as such:
```
Section "Monitor"
	Identifier	"SyncMaster"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1440x900@60"
	EndSubSection
EndSection

```

I had a very silmilar problem with Feisty when I origionally got the monitor, but was able to resolve it by installing 915resolution from the Synaptics Package Manager.  I've tried doing this again, and it does not do anything, even after a restart.  

Any help?

---

### Post by moonshinerat on 2008-03-03
Hi,

Can I just ask if you have a solution to this because I have just bought the same monitor and have the same problem, only difference is that I'm on an Intel chipset?

I would really appreciate it if you have solved this and can forward your solution.

Many thanks,

Moonshinerat

---

### Post by heatpumpcontrol on 2008-07-07
Hey guys,

I've discovered that if you just use the nvidia settings control panel instead of the System->Preference->Screen Resolution option then you can obtain the desired graphics display. That is what I'm using right now in Gutsy. Should be the same in Hardy.

---

