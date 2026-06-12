---
title: "Video Card Driver Problem"
date: 2009-04-07
forum: Hardware
---

### Post by rte24 on 2009-04-07
I have a graphics problem on a very old biostar motherboard model m6twg with onboard intel video chipset 82810.  Ubuntu has loaded the driver for the video card and I get the resolution I want (1028x728) but dvd playback is choppy and the computer overall acts like the video driver isn't right(windows move choppy, scrolling choppy, etc).  

Also, ubuntu will let me enable desktop effects, but when I do the menu bars disappear and I get the white terminal.  I have a few other ubuntu builds under my belt, and have solved this problem before with an nvidia geforce 4 by editing my xorg.conf file.  However, my xorg file on this system appears to be completely generic:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

That's all that is there and I don't know what that means.  I've went into synaptec and made sure all the intel 810 packages were installed, and tried to rebuild my xorg file, but still made no progress.  I don't care much about desktop effects, but do need dvd playback to be smooth.  I realize this is a very old system, but it's for a friends mom and it will be plenty for her.  Any suggestions?

---

### Post by Sam Lars on 2009-04-09
I don't think that card will support Compiz... there may be some way to get it to work, you could search into that.
On the same note, it's not going to be the snappiest when moving windows, etc.

---

### Post by DJonsson2008 on 2009-04-09
If you can scrape up 20 - 40$ buy a better supported Nvidia,
Graphics card, I wrestled with my onboard IBM graphics 
with no effect. Its better wrestling with a known and supported
Nvidia card and in the end getting better control and better 
performance.

The Envy or envyng script makes installing nvidia relatively
easy, there will possibly be issues in getting it installed
but in the end you will have a better machine.

---

