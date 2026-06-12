---
title: "Resolution problem with fresh install of Xubuntu 11.04"
date: 2011-07-29
forum: Hardware
---

### Post by paranormal on 2011-07-29
I just did fresh install of Xubuntu 11.04 on my old desktop ( Intel P4 2.4 ghz with intel 865 chipset). Im having a problem with the screen resolution. I have a 19" wide screen monitor and the desired resolution is 1440 x 900, but the max i can get right now is 1024 x 768. I did my "googling" and found that this problem can be solved by editing /etc/X11/xorg.conf.To my surprise the file dint exist, so i manually created the file (doing "Xorg -configure" in the recovery mode dint work in my case either) and added the settings on my own.No prizes for guessing .... this dint solve my problem.Though the max refresh rate which was previously at 61.1 Hz is now up to 85.0 Hz :D but the max resolution is still 1024 x 768 :(.

Im posting my xorg.conf file here ... someone please help me figure out the problem

```
Section "Device"
	Identifier    "Configured Device"
EndSection

Section "Monitor"
	Identifier    "Configured Monitor"
	HorizSync      30-96
	VertRefresh    50-160
	Modeline      "1440x900_75.00"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync
	Option				"PreferredMode" "1440x900_75.00"
EndSection

Section "Screen"
	Identifier    "Single Screen"
	Device        "Configured Device"
	Monitor       "Configured Monitor"

	SubSection    "Display"
		Depth       24
		Modes  	    "1440x900" "1360x768" "1024x768" "800x600" "640x480"
	EndSubSection

	SubSection    "Display"
		Depth       32
		Modes  	    "1440x900" "1360x768" "1024x768" "800x600" "640x480"
	EndSubSection

EndSection

```

also posting lspci output

```
~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

Help Me !!

---

