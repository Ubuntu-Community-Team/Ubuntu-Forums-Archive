---
title: "Gateway Solo 9500 Two Monitors One Screen"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by jquigley2 on 2007-11-20
I have been able to load 7.10 on my Gateway Solo 9500, however I now have 2 monitor screens on my one screen making it very hard to read. Any ideas would be gratefully accepted. I have beat my head against the wall for a couple of hours and don't know what else I can do with this.](*,)

---

### Post by gdzsi on 2007-11-21
post your /etc/X11/xorg.conf !

---

### Post by ayuffa on 2007-12-21
Here are some solutions to common screen/monitor problems with Gateway Solo 9500.  They worked on Gutsy Gibbon but will *probably* work on Feisty Fawn as well.  [B]Before you start I recommend setting all xserver values to their default values via 
```

dpkg-reconfigure -phigh xserver-xorg

```
[/B]
[LIST=1]
[*]Problem:  Screen flickers and/or you have "2 monitor screens on one screen" 
[*]Solution:  You need to change ati driver to vesa driver in /etc/X11/xorg.conf
```
 
Section "Device"
	Identifier	"ATI Technologies Inc Rage Mobility M4 AGP"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

```
[/LIST] 
[LIST=1]
[*]Problem:  Screen resolution.  The default is 800x600 which is way too low.
[*]Solution:  Change screen resolution to 1024x768 (I couldn't get 1280x1024 resolution to work, if you do, please post)  You will need to change two things in xorg.conf file, i.e., refresh rates and screen resolution. 
```
 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

```
and
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage Mobility M4 AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

```
[/LIST]
Now restart your xserver via Ctrl-Alt-Backspace or by rebooting your computer.  If you are not happy with the resolution you should now be able to change it via kcontrol or krandrtray (note krandrtray will dock to right hand side of your panel).  If something goes wrong don't worry just run 
```

dpkg-reconfigure -phigh xserver-xorg

```
and that will wipe out any changes you have made.
thanks,
yuffa

P.S. If the above doesn't work for you you may find [thread=322192]this thread[/thread] helpful.

---

