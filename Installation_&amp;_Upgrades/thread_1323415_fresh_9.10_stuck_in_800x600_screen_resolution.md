---
title: "fresh 9.10 stuck in 800x600 screen resolution"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by sharp11 on 2009-11-11
Like a number of others, I did a fresh install of 9.10 and found that I was not offered any higher screen res than 800x600. Since I use a ViewSonic VX1940W (widescreen) LCD whose native resolution is 1680x1050, this really sucked. I'm guessing this may have been caused by my fairly old graphics card (ATI Rage 128 ) - but it's only a wild guess. I have used that card with prev versions of ubuntu w/o this problem.

First thing I tried was dpkg-reconfigure xserver-xorg. Turns out this is a no-op (ie. does absolutely nothing) in 9.10 (maybe bc there is no xorg.conf?). 

Then I tried creating a new xorg.conf from scratch using xrandr. I was able to add new modes via xrandr, but when it came time to use them, I just got the error msg: Failed to change the screen configuration!

Finally, what worked was that I had an old hard drive with an old version of ubuntu that I had upgraded to 9.10 a while ago. It never ran well, but it had an xorg.conf file. I installed that file in /etc/X11/, restarted X and everything came up fine. 

For those who may not be so lucky as to have an old xorg.conf lying around, here's the contents of mine (your graphics card will probably be different, but most of the rest is generic):

> Section "Device"
	Identifier	"ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128]"
	Driver		"ati"
	BusID		"PCI:0:9:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 PP/PRO TMDS [Xpert 128]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

---

