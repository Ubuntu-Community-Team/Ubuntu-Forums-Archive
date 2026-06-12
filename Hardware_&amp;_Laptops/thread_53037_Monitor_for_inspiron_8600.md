---
title: "Monitor for inspiron 8600"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by umdzig on 2005-07-30
I just installed a new driver for my ATI Radeon 9600 and i need to know what to put in the xorg.conf file for the monitor so i can get my desired screen resolution. I have a dell inspiron 8600 laptop.


Already failed twice at it...and was left with only the command line. But i managed to fix that

---

### Post by heimo on 2005-07-30
This could help:
[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

If you can send us more information (error messages / logs) and relevant parts of xorg.conf, it'll be easier to suggest solutions.

---

### Post by amohanty on 2005-07-30
install fglrx via synaptic.

>> sudo fglrxconfig

---

### Post by umdzig on 2005-07-30
[QUOTE=heimo]This could help:
[http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984)

If you can send us more information (error messages / logs) and relevant parts of xorg.conf, it'll be easier to suggest solutions.[/QUOTE]

Ok here is an excerpt from my xorg.conf file: 
--------
Section "Monitor"
	Identifier	"NEC E1100+"
	Option		"DPMS"
	HorizSync	31-96
	VertRefresh	55-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"NEC E1100+"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
---------------

I dont have an NEC E1100+, however that is the only one that i can think of that allows me to boot into the ubuntu w/o having just the command line.

I have a Dell inspiron 8600 notebook so i dont know what my monitor would actually be. With the setup i have now i can only view my screen at 1280X1024, i know i can use the 1600X1200, it worked in before i installed the new driver now it doesnt.

---

### Post by heimo on 2005-07-30
Hmm... is this helpful?
[http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html](http://www-zeuthen.desy.de/~alorca/linux2onlaptop.html)

You could try:
  ```

Section "Monitor"
  Option       "CalcAlgorithm" "CheckDesktopGeometry"
  DisplaySize  332 207
  HorizSync    30-33
  Identifier   "Monitor[0]"
  ModelName    "7T774^D154P1 MONITOR"
  Option       "DPMS"
  VendorName   "SEC"
  VertRefresh  43-72
EndSection
``` 
change the Identifier to match Monitor line in your Screen section.

---

### Post by umdzig on 2005-07-30
Thanks your link was helpful. I had the wrong screen resolution for my monitor in my xorg.conf file. Apparently i needed 1680x1050 not 1600x1200. Although now since i installed the new driver for my ati card my computer runs slower. Any ideas for that one? I used the fglrx driver via synaptic since the one from ATI's website didnt seem to work.

---

### Post by heimo on 2005-07-30
Great you solved the resolution problem! I don't know much about ati drivers, maybe someone else can help on those. Check that you didn't miss anything.

Some threads:
[http://ubuntuforums.org/showthread.php?t=32495](http://ubuntuforums.org/showthread.php?t=32495)
[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

---

