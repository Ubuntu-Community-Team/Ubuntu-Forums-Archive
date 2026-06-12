---
title: "In need of modline help for my HTPC"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by MetalMusicAddict on 2007-01-09
I have a HTPC Im trying to move from windows. I dualboot XP and
Ubuntu-Edgy on it. In windows I run it at 1280x720@60hz. In linux I cant get
it to move from 1280x768@60hz.

Im running a nVidia 6800 in it.

So I need help with creating the correct xorg modline. Ive seen examples
but they confuse the hell out of me.

If I could get this sorted it would be the 2nd to last issue to solve to
get 1 more PC in my home to linux only. The other issue being getting
AC3 sound out of my SPDIF correctly. ;)

```
[SIZE="1"]Section "Device"
	Identifier	"NVIDIA GeForce 6800"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	30-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6800"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection[/SIZE]
```

---

### Post by hal10000 on 2007-01-10
Your problem may be fixed by just adding [COLOR="Red"]"1280x720"[/COLOR] to (every) [COLOR="Red"]Modes[/COLOR] line.

But i suggest the propper way to reconfigure your xserver: in a terminal window type: [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] and follow the steps in the program. You might say yes to the most questions and may autoprobe monitor, modelines, keyboard, etc. Don't forget to select the [COLOR="Red"]nvidia[/COLOR] driver module, as per default it only selects the "nv" module which offers no 3D hardware acceleration. When it askes for easy, medium or advanced Display settings, you may select the medium option (perhaps you can get you monitor to more than 60 Hz, it then is more friendly to your eyes). If you know the exact settings for horizontal and vertical refresh (from your monitor's manual) you may select the advanced option and type in the correct setings.

Your existing /etc/X11/xorg.conf will be backuped, so you can restore it if anything goes wrong.

---

### Post by MetalMusicAddict on 2007-01-10
> **hal10000 said:**
> Your problem may be fixed by just adding [COLOR="Red"]"1280x720"[/COLOR] to (every) [COLOR="Red"]Modes[/COLOR] line.

But i suggest the propper way to reconfigure your xserver: in a terminal window type: [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] and follow the steps in the program. You might say yes to the most questions and may autoprobe modelines, keyboard, etc. Don't forget to select the [COLOR="Red"]nvidia[/COLOR] driver module, as per default it only selects the "nv" module which offers no 3D hardware acceleration. When it askes for easy, medium or advances Display settings, you may select th medium option.

Your existing /etc/X11/xorg.conf will be backuped, so you can restore it if anything goes wrong.

Sorry, thats all been done. I know this hardware can do it. I do it in windows. I just dont know how to get it to work in linux. I wonder if theres a way to use any of the info from windows? :-k

---

### Post by hal10000 on 2007-01-10
But the "1280x720" doesnt appear in the Modes line. 
If i were you, i would just try to replace [COLOR="Red"]"1280x768"[/COLOR] by [COLOR="Red"]"1280x720"[/COLOR]. If you replace it then 1280x720 is the default (and max.) resolution. 
If you add it instead of replacing then you may change the resolution by pressing <CTRL>+<ALT>+<+> (on the numeric keys block) together
or by using [COLOR="Red"]xvidtune -next[/COLOR].

---

### Post by MetalMusicAddict on 2007-01-10
> **hal10000 said:**
> But the "1280x720" doesnt appear in the Modes line. 
If i were you, i would just try to replace [COLOR="Red"]"1280x768"[/COLOR] by [COLOR="Red"]"1280x720"[/COLOR]. If you replace it then 1280x720 is the default (and max.) resolution. 
If you add it instead of replacing then you may change the resolution by pressing <CTRL>+<ALT>+<+> (on the numeric keys block) together
or by using [COLOR="Red"]xvidtune -next[/COLOR].

Its not in there now because it doesnt work. ;) If I do add it it defaults to 1024x768.

---

### Post by hal10000 on 2007-01-10
I have no idea, sorry

Perhaps you should install (and compile) the latest nvidia driver from the nvidia website. If you do, you have some packages to be installed (gcc, xserver-xorg-dev, binutils, kernel-headers (appropriate to your running kernel) and maybe some others too). But take in mind, that every time you change to another kernel, you have to recompile the driver. Also the nvidia installer program does it only on a console, so you have to shtudown you xserver and run the install process from the command line.

---

### Post by MetalMusicAddict on 2007-01-10
Looks like beat you to the punch on everything. Im running Feisty and it currently has the newest  nvidia driver. Im sure its not a driver issue. Its just finding the right modline.

Something like [THIS]("http://www.turnpike420.net/linux/Samsung_DLP_xorg.conf_sample.txt") is what I gotta do. If I dont get the timings right though I could mess up my plasma. Dont want to do that now. ;)

---

