---
title: "Weird resolution issue in Karmic"
date: 2010-01-09
forum: Hardware
---

### Post by volksman on 2010-01-09
Hey All!

I have a strange issue in Karmic.  I have an i810 Intel card and a 22" Samsung flat screen. 

I use a 15 ft cable normally as it is fished through a wall.  However in Karmic my max res (after using kernel 2.30.9 and a custom xorg.conf file) is 1360x768.

If I attach a standard 4ft cable it will push max res at 1680x1050.  Which is what I want.

If I boot with the 4ft cable and swap in the 15ft cable everything continues to work at high res, no issues.  Obviously I don't want to have to swap cables everytime I reboot.

So how can I force the modes in Karmic.  Here is my xorg.conf as it stands:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" # i8xx users: see note in guide
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
	Modeline "1680x1050@60" 119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync
EndSection

```

---

### Post by diesch on 2010-01-10
The follwing pages may help you:

[LIST]
[*] [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
[*] [https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)
[*] [https://wiki.ubuntu.com/X/MonitorDetection](https://wiki.ubuntu.com/X/MonitorDetection)
[/LIST]

---

### Post by volksman on 2010-01-10
Thanks that first one was pretty helpful for my needs I think.  However I already rebuilt with Jaunty to see if it would make a difference.  And it doesn't out of the box but my xorg.conf works so I have a workable desktop.

Now I wonder if I should upgrade to Karmic again since the 3d performance in Jaunty with my chipset is terrible and I've read rumors of the new intel driver in Karmic being better.

Any comments or articles I could read to help make this decision?

Thanks in advance!

---

