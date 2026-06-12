---
title: "After upgrade to 9.10, Thinkpad monitor gets vertical stripe when using dual monitor"
date: 2009-05-09
forum: Hardware
---

### Post by lsiden on 2009-05-09
Just upgraded my Thinkpad R52 to Jaunty Jackelope 9.04.  When I insert a second monitor (Acer, w/ 1280x1024 res), the laptop monitor has a vertical stripe smack in the middle that goes from top to bottom of the screen, and another stripe on the far right edge of the laptop monitor.  I wanted to include a screenshot, but of course, it doesn't show up on the screenshot b/c it has to do only with monitor settings.

Because I can see fragments of images in each of the vertical stripes, I am guessing that this must be some kind of horizontal syncing issue.  I tried running xvidtune, but every time I tried to change something, a box popped up saying that my h/w doesn't support the new setting.

Here is what lspci shows for my display adaptor:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

My xorg.conf file is pretty minimal.  FWIW, here it is:

Section "Monitor"
	Identifier	"Configured Monitor"

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2560 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

