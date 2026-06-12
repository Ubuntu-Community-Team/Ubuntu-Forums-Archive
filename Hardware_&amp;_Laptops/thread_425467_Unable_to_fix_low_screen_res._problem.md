---
title: "Unable to fix low screen res. problem"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Crashing on 2007-04-27
I found a document on the Ubuntu wiki website that tells how to deal with Fiesty's not being able to drive monitors at higher resolutions than 1024x768 by default. I first tried to edit my xorg.conf file like the article said to do. I added "1600x1200" as an option wherever resolution related numbers came up. here's what my Xorg.conf file looks like:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 RF/SG AGP"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection
```
Before I go anyfurther, I should include some system specs:
ATI Rage 128 AGP graphics card which can drive monitors up to 1800x1440
Viewsonic E90fb monitor which can go 1600x1200 or a max of 1792x1344
When modifying that didn't work, i tried restarting the X server but that didn't help either.
I tried "aticonfig" but I don't have the fglrx driver. If I need that driver, how do I install it? Apt-Get??

---

### Post by thelocust on 2007-04-27
**[COLOR=Red]sudo apt-get install xorg-driver-fglrx[/COLOR]**

Then I did these:
**[COLOR=Red] sudo aticonfig --initial[/COLOR]**
**[COLOR=Red] sudo aticonfig --overlay-type=Xv[/COLOR]**

Finally, **[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]**, selecting the _**fglrx**_ driver and setting my monitor resolution how I wanted it

Then reboot and thats it.

---

### Post by Crashing on 2007-05-04
> **thelocust said:**
> **[COLOR=Red]sudo apt-get install xorg-driver-fglrx[/COLOR]**

Then I did these:
**[COLOR=Red] sudo aticonfig --initial[/COLOR]**
**[COLOR=Red] sudo aticonfig --overlay-type=Xv[/COLOR]**

Finally, **[COLOR=Red]sudo dpkg-reconfigure xserver-xorg[/COLOR]**, selecting the _**fglrx**_ driver and setting my monitor resolution how I wanted it

Then reboot and thats it.I have reconfigured my x-server about 5 times but the fglrx driver doesn't work. in a different thread, someone told me to do this:
> **zvacet said:**
> Boot up in recovery mode nad type 

```
dpkg-reconfigure xserver-xorg
```

Select **vesa** and after your graphic works go and find proper drivers for your card.
It works but the screen flickers a LOT even when I had it set to 1600x1200 75Hz or 60Hz. Is it just some sort of driver used for system recovery? if so, what driver should I use? I am seeing an option for 1224x1024 now but it isn't any different from 1024x768.

---

### Post by Crashing on 2007-05-04
I somehow missed the ATI driver but now I am using that one and it works. I can go all the way up to 1600x1200 now but I want to do a 70Hz sync rate instead of 60Hz the monitor still flickers but it isn't near as bad. I found a driver specifically for the rage 128 series but I can't install it by doing ```
Sudo Apt-Get Install xorg-driver-r128
``` How do I install it?

---

