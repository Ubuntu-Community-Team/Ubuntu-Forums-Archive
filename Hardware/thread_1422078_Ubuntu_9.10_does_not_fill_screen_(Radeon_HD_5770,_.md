---
title: "Ubuntu 9.10 does not fill screen (Radeon HD 5770, 1920x1080)"
date: 2010-03-05
forum: Hardware
---

### Post by ckth on 2010-03-05
I installed Ubuntu 9.10 on my desktop, which has a 21" monitor with a resolution of 1920x1080. 

I installed the ATI drivers and Catalyst control center for my HD 5770, and Ubuntu works OK.

However, even at 1920x1080 at 60HZ, the screen is not filled and there are black bands around the desktop. Here's an image that hopefully explains what's going on:

[[img]http://omploader.org/tM3Fsag[/img]](http://omploader.org/vM3Fsag)

About 10% of the screen is unfilled in both directions. Attempting to stretch the image using the monitor settings was not helpful.

Any ideas?

Here's my xorg.conf:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by lidex on 2010-03-05
A wealth of info on this page:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

I'm more familiar with nvidia, but that should point you in the right direction.

Here's a similar problem:
[http://ubuntuforums.org/showthread.php?t=872330]("http://ubuntuforums.org/showthread.php?t=872330")

---

### Post by dert on 2010-03-26
FYI.  The same thing happens in Windows 7 on my 37" HDTV.  Black Border all around.  It's an ATI (or AMD or whatever they're called now) driver issue not an Ubuntu issue.  I have the 5770 too with a dual boot Ubuntu Studio 9.10 and Windows 7.  Both operating systems have the same behavior.  I zapped a note to their support folks letting them know.

For now, the 2nd link in the post above contains very helpful information on a workaround.  He essentially created a custom display resolution that takes up the full screen without sacrificing text/image quality.  It worked for me!

BTW, that RadeonDriver page references some pretty old cards.  I believe an update may be in order.

---

### Post by nynexman4464 on 2010-07-29
I had this problem.  I also had it in windows when I first installed. I think the driver detects the display as a TV (which mine actually is) and enables the "underscan" setting.  This is completely unnecessary on a digital screen.

You have to use the ATI drivers (it's the only way I can get a display over HDMI anyhow).

To fix it, go into the Catalyst Control Center (with root privileges), find the display under "display manager" (EX mine is "DTV (1)" ).  Click the "Adjustments" tab.  There should be a slider "Scaling Options".  Slide it all the way over to "Overscan" (0%).  That should fix it.

---

### Post by ckth on 2010-07-30
> **nynexman4464 said:**
> I had this problem.  I also had it in windows when I first installed. I think the driver detects the display as a TV (which mine actually is) and enables the "underscan" setting.  This is completely unnecessary on a digital screen.

You have to use the ATI drivers (it's the only way I can get a display over HDMI anyhow).

To fix it, go into the Catalyst Control Center (with root privileges), find the display under "display manager" (EX mine is "DTV (1)" ).  Click the "Adjustments" tab.  There should be a slider "Scaling Options".  Slide it all the way over to "Overscan" (0%).  That should fix it.

Do you mean the ATI drivers that show up in the restricted drivers utility in Ubuntu, or the ATI drivers that you can download and install via a script from the AMD website?

I am using the former, and I don't see any "Scaling Options" slider.

---

### Post by ckth on 2010-07-31
Here's what the display manager tab looks like. I don't see an "Adjustments" or "scaling options" button.

[IMG]http://omploader.org/tNTNvZg[/IMG]

EDIT: D'oh. Found it. It works. Thanks!

---

### Post by hlainchb on 2010-12-23
> **nynexman4464 said:**
> I had this problem.  I also had it in windows when I first installed. I think the driver detects the display as a TV (which mine actually is) and enables the "underscan" setting.  This is completely unnecessary on a digital screen.

You have to use the ATI drivers (it's the only way I can get a display over HDMI anyhow).

To fix it, go into the Catalyst Control Center (with root privileges), find the display under "display manager" (EX mine is "DTV (1)" ).  Click the "Adjustments" tab.  There should be a slider "Scaling Options".  Slide it all the way over to "Overscan" (0%).  That should fix it.

Thank you for posting this.  I was going insane trying to figure out what was wrong.  Your post was exactly what I needed to fix my display issue.

---

### Post by mbching on 2012-02-29
oh my god thanks a lot it helps!!!

---

