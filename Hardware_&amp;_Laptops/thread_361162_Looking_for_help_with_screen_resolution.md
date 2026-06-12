---
title: "Looking for help with screen resolution"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by czechrm on 2007-02-14
hey all,
i am totally and completely new to the whole Linux thing, and absolutely love it.  however, i am running a Toshiba Satellite U205-S5002 laptop with a normal 1280X800 screen resolution.  But, when I run Ubuntu, the resolution seems to be too big for the screen, so i have to run the smaller size that contorts the screen.  after searching the forums, i found an optional install for the 915resolution for Intel chipsets, but i cannot find the package in the terminal or through synaptic.  if anyone has any ideas, i would love to hear them so i can get this cleaned up!!  thanks in advance for the help.

---

### Post by mikewhatever on 2007-02-14
I do not know about 915 resolution, whatever that may be, but while waiting for someone who does, can you post the output of the following
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by czechrm on 2007-02-14
hope this helps - it's the screen part of the xorg.conf file

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

---

### Post by mikewhatever on 2007-02-14
Thanks, there is nothing to change there, since the resolution is correct. However, while looking for something different in synaptic, I found the package you've mentioned before (915resolution) It is on the very first page, see the screenshot.

---

### Post by czechrm on 2007-02-14
thanks for posting the screenshot...  I just finished updating everything in the 6.10 system.  Mike, what system are you running??  The 915resolution still does not show up in the Synaptic folder. is there some kind of update that i am missing??

---

### Post by redoscar3 on 2007-02-14
The 915resolution package is in the "universe" repositories for Ubuntu.  If you are using Ubuntu 6.10, make sure you use the repository for Edgy.

Check "Repositories" in Synaptic and see if "universe" and "multiverse" are available.  If so, you can add them, then update you package list and locate the desired package using "Search".

Good luck,

Red

---

### Post by czechrm on 2007-02-15
ok....
i downloaded and installed the 915resolution files.  now what??

---

### Post by czechrm on 2007-02-18
this is a bump - guys i really need a hand here.  I have been searching for info on this FOREVER!!!  I need help with the 915resolution.  I have followed install scripts and several things including editing my xorg.conf file to reflect a Modeline for the resolution - but it still doesn't frickin' work!!!  I'm tearing my hair out here!!! HELP!!!

---

### Post by czechrm on 2007-02-20
Bump!!! Help!!!

---

### Post by redoscar3 on 2007-02-21
I don't have your hardware configuration, so I can't speak from experience.  But the following link gives instructions on what to do after installing the 915resolution package.

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

Hopefully this gets things going for you.  Beyond this, I would be at a loss to know what else to advise.

Red

---

### Post by ramjet_1953 on 2007-02-22
Follow this link and all should be revealed.

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Regards,
Roger :cool:

---

