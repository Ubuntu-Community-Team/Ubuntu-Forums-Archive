---
title: "Help with IBM Thinkpad video"
date: 2009-03-31
forum: Hardware
---

### Post by tlowery on 2009-03-31
Hello, I'm hoping someone here can help me with a video problem I'm having on my IBM Thinkpad R51 after upgrading from Hardy to Intrepid.  On Hardy my video was working fine at 1280x1024 without 3d exceleration (visual effects could not be enabled on gnome desktop), but the screen responsiveness was very acceptable (Google Earth was very responsive).  After upgrading to Intrepid I was left with 1024x768 resolution, but graphics acceleration seemed to be working (visual effects could be enabled in gnome desktop).

I wanted to try to get my 1280x1024 resolution back so I experimented with different drivers.  lspci reports that my video hardware is:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

So I tried installing the xserver-xorg-video-radeon driver.  Now when I boot the system the xserver starts with the bare 'X' cursor and I am eventually prompted with:

"Ubuntu is running in low graphics mode.  Your screen graphics card and input device could not be detected correctly."

I click OK and I'm given the following choices:

1. Run Ubuntu in low graphics mode
2. Reconfigure graphics
3. Troubleshoot.

Choosing option 2 results in a hung system with a blank screen.  Choosing option 3 displays some log files that weren't very helpful (probably my inexperience).  Choosing option 1 eventually gets me to the Ubuntu gnome login screen and my desktop at 1280x1024, but very slow screen rendering.

My xorg.conf file looks like this:

> 
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Which seems kind of odd.

Is there a way to force Ubuntu to "re-discover" my video hardware and get me back to the 1024x768 that was working reasonably well?  Even better, is there a way to get the 1280x1024 resolution with acceleration that I had with Hardy?

Thanks in advance for any assistance.

Tim

---

### Post by hobo on 2009-03-31
Check this site and this page it may be of some help:

[http://http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500]("http://http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500")

---

