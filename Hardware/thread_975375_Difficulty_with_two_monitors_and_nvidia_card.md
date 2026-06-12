---
title: "Difficulty with two monitors and nvidia card"
date: 2008-11-08
forum: Hardware
---

### Post by janus113 on 2008-11-08
Hi.  I'm rather new to linux but have been playing around with the xorg.conf file since installing with the help of a friend because I run the dreaded nvidia card duel monitor set up.  I managed to get it working ok, and then I purchased a new (bigger) monitor.

I have the nvidia drivers (successfully?) installed, and the way I managed to set my screen resulutions was by adding some sections to the xorg.conf.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2304 864
	EndSubSection
Option "TwinView"
Option "MetaModes" "1680x1050 1280x1024"
EndSection

I just added those last two lines of code.  It "seems" to work, but my new monitor tells me its running at a lower resolution than I've set in the xorg.conf; plus everything looks freaking huge compared to my second monitor.  My main question is; how can I edit this xorg.conf so that I can have two monitors running at...
1680x1050
and
1280x1024.

I have a sneaking suspicion that my second monitor is running slightly below the resolution I've told it to.  I don't understand that config file enough to screw around with it, so I'm trying to stay away from the other threads that set up monitor resolutions, because I don't think I can make the required adjustments for my settings without screwing something critical up.

Thanks.

Ubuntu 8.10
Nvidia 177 drivers with 8600 Card
22 inch widescreen with 19 inch secondary monitor.

---

### Post by phidia on 2008-11-08
Make sure you have the nvidia-settings package installed then use that gui to set your 2nd monitor up.

---

### Post by janus113 on 2008-11-08
I have that installed, and doing anything in the gui always fails to have a lasting result; also, my desired resolution settings are not available for selection in the gui.

---

### Post by janus113 on 2008-11-08
I think I figured out the first step of my problems... at least to let me monitor run at full resolution.  I just changed xorg.conf to this...

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2960 1050
	EndSubSection
Option "TwinView"
Option "MetaModes" "1680x1050 1280x1024"
EndSection

All I changed was the virtual part under the subsection display.  It occured to me if linux was treating my whole setup as one monitor, it better be thinking its going to be the right size.

My next problem/question though, is I downloaded the quake version for linux...and it treats my entire space as one monitor too.  This is bad, seeing as how it loads right between my monitors.  Is this twinview's fault?  Should I try and have it treat each monitor as its own desktop?  I've only done this stuff in windows, which just automatically sets it all up, so I'm still a bit lost at the linux aspect.

---

