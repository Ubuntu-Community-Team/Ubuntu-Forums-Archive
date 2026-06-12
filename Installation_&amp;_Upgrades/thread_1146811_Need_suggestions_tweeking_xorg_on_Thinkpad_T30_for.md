---
title: "Need suggestions tweeking xorg on Thinkpad T30 for Jaunty"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by poit on 2009-05-02
At least I think that's what I need. I had it working pretty good on 8.04, but with Jaunty graphics are slow, system runs hot, you know...the usual complaints on this forum. 

So, my Thinkpad uses an ATI Mobility 7500. glxgears gets around 700, but Firefox doesn't scroll smoothly any more, and flash uses 100% resources, the CPU quickly rises from 40 to 70 cent. Graphics just generally feel slower and jerkier.  Here's my current Device settings in xorg:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "AccelMethod" "XAA"
		
EndSection
```

These changes made things slightly better but still not right. I gathered this stuff from various posts. Anyway, if anyone has any ideas to improve performance on this old laptop (other than "BUY A NEW ONE") I'm interested.

Thanks

---

### Post by kerry_s on 2009-05-03
you should check out think wiki, it's the best help for think pads.
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

[http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)

---

### Post by poit on 2009-05-03
> **kerry_s said:**
> you should check out think wiki, it's the best help for think pads.
[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)

[http://www.thinkwiki.org/wiki/Category:T30](http://www.thinkwiki.org/wiki/Category:T30)

Been there. They don't have any help beyond 8.04, and it sure seems what worked in 8.04 doesnt work on Jaunty

---

### Post by poit on 2009-05-03
Just an update here. I've been continuing to tweek the xorg.conf file based on lots of posts from lots of websites. Right now I've got the glxgears up to about 800 fps and Firefox seems to have smoothed out. I don't have any basis for what I've done other than trial and error, I really don't understand what alot of these options do. Anyway, here is what my xorg.conf looks like now:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "AccelMethod"    "XAA"	
	Option "AGPMode" "4" 
	Option "AGPSize" "64"
	Option "RingSize" "8"
	Option "BufferSize" "2"
	Option "EnablePageFlip" "true"
	Option "EnableDepthMoves" "true"
	Option "RenderAccel" "true"
	# Eyecandy Stuff
	Option "AccelMethod" "4"
	Option "DDCMode"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

I'd love to have more info if anyone has it, and maybe this will help someone else.

---

### Post by upchucky on 2009-05-03
if you have accelerated graphics, glxgears should be reporting between 10,000 and 13,000fps,
depending on what I am doing i can get 16,000fps

electric@XPS-Laptop:~$ glxgears
57484 frames in 5.0 seconds = 11496.777 FPS
76768 frames in 5.0 seconds = 15353.456 FPS
65830 frames in 5.0 seconds = 13165.992 FPS
81776 frames in 5.0 seconds = 16355.160 FPS
75569 frames in 5.0 seconds = 15113.739 FPS
75952 frames in 5.0 seconds = 15190.288 FPS
79967 frames in 5.0 seconds = 15993.356 FPS
80101 frames in 5.0 seconds = 16020.091 FPS
80758 frames in 5.0 seconds = 16151.445 FPS
80938 frames in 5.0 seconds = 16187.577 FPS
81102 frames in 5.0 seconds = 16220.267 FPS
71037 frames in 5.0 seconds = 14207.340 FPS
65401 frames in 5.0 seconds = 13080.098 FPS
73002 frames in 5.0 seconds = 14600.222 FPS

---

### Post by poit on 2009-05-04
> **upchucky said:**
> if you have accelerated graphics, glxgears should be reporting between 10,000 and 13,000fps,
depending on what I am doing i can get 16,000fps


Glad you've got such a screamin' system, but I'm using a 6 year old Thinkpad T30 with a ATI Mobility 7500 graphics chip. I've never gotten better than about 860 FPS with any version of Ubuntu. Without any hacks in the xorg.conf I get about 650, so at least now I get smooth scrolling on firefox again.

---

### Post by MysteriousHoatzin on 2009-07-05
Just wanted to add that cutnpasting your xorg conf (I just had to add some stuff for extending the virtual desktop) solved a weird video memory allocation bug I had with my T30: it wouldn't play video files larger than a certain arbitrary size (as in x by y pixel dimensions rather than disk space)--this included DVDs. I'll paste it here so that people searching for this error can know this will be of help:

```
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

T30 is such an unfortunate orphan: IBM abandoned it, Lenovo doesn't care; ATi never cared, and AMD doesn't wish to retroactively change that.

---

