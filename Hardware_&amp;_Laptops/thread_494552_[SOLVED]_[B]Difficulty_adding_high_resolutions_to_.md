---
title: "[SOLVED] [B]Difficulty adding high resolutions to Samsung 226BW monitor[/B]"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by twin_57103 on 2007-07-07
I've recently added a Samsung 226BW 22" widescreen monitor (upgraded from a 17" which was used during installation), but I'm having trouble getting the resolution above 1280x1024.  I know that this is a common problem, but I've been having trouble sorting it out from the other threads I've read (most seem to apply to the Intel 915 fix).  My goal for this monitor is graphic editing/photo restoration, and getting the resolution up is important.

My video card is Radeon X300/X550 (128Mb RAM).  I am dual booting XP and Feisty Fawn.  The monitor runs at 1650x 1050 under Windows, so the hardware appears compatible.  I am currently using the proprietary Radeon driver (installed as a troubleshooting step for this problem).

Here are the applicable lines from lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

I've attempted to use dpkg-reconfigure xorg.  It appears that the process has detected the higher resolutions (see xorg.conf below), but the Screen Resolution box gives only 1280x1024, 1024x768, and 800x600 as options.

Here is the monitor section of my xorg.conf file:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

I'd appreciate any help you could offer.  I'm still pretty new to Linux and Ubuntu (but enjoying them!).  Thanks!

---

### Post by h-bomb on 2007-07-07
Hello, I'm having the same problem with the same monitor, Similar output. Any input would be greatly appreciated.

---

### Post by h-bomb on 2007-07-07
Hi agian, one difference i noticed is that i have a nvidia graphics card. for giggles i typed nvidia settings in the terminal and the nvidia configuration menu came up. i was able to change my settings from there. I hope you solve your problem soon.

---

### Post by twin_57103 on 2007-07-07
> **h-bomb said:**
> Hi agian, one difference i noticed is that i have a nvidia graphics card. for giggles i typed nvidia settings in the terminal and the nvidia configuration menu came up. i was able to change my settings from there. I hope you solve your problem soon.

So far I haven't found a comparable command for my Radeon.  I'd welcome any input on how to proceed-it looks like the resolutions are there, but I simply don't have the option to select them.  It's still an improvement over what I had, but there ought to be a way to get it to work.

---

### Post by twin_57103 on 2007-07-07
I finally got it.  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")
has some useful information.  I was able to use it to update the driver.  The screen looks normal again-not stretched!  Thanks for the help.

---

