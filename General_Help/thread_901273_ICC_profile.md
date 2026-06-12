---
title: "ICC profile"
date: 2008-08-26
forum: General Help
---

### Post by uid313 on 2008-08-26
I bought a new 24" monitor.

How do I load the ICC profile?

---

### Post by pvalley1967 on 2008-08-26
how bout checking here 

[http://www.scribus.net/](http://www.scribus.net/)

hope this helps

---

### Post by uid313 on 2008-08-26
Sorry, Scribus is just a publishing software with ICC support.
I want system-wide ICC support all over the whole graphical system and all applications.

---

### Post by john_navarro on 2008-10-14
Get the software from here:
[http://www.argyllcms.com/](http://www.argyllcms.com/)

You'll also need some type of calibration hardware - I use a DTP94 type device.

_To Profile The Display_

1) Set env. variable:
export ARGYLL_IGNORE_XRANDR1_2=yes

2) Profile the display:
dispcal -yl -K -t6500 -f1 -k0 -o samsung.icc

3) Install Profile into X11 atom (this survives reboots):
dispwin -I samsung.icc


_Every time you boot_

1) Set env. variable:
export ARGYLL_IGNORE_XRANDR1_2=yes

2) Load profile into X11:
dispwin -L


NOTE: You may get strange color casts if you don't do the "export ARGYLL_IGNORE_XRANDR1_2=YES" before running the "dispwin -L"


_Other Notes_

dispwin -c                         (clears profile)
dispwin &#8211;V samsung.icc  (verified profile is loaded)

&#8220;dispwin -I&#8221; installs your profile in an x11 atom. A file is created called .config/color.jcnf

And the profile itself is copied to .local/share/color/icc/devices/display/ 

To verify the X11 atom is loaded - comma after -d is needed:
xprop -root | grep ICC | cut -f 1-10 -d,


**Screen Savers**  (credit: lt_gustavsen; user from bibblelabs support forum)
If you are using gnome-screensaver it will destroy your calibration if you don't stop it before you load the calibration. I think gnome-screensaver remembers the status of the LUT from the time X11 was started. This script:

	#!/bin/bash
	#Profile installed once with:
	#dispwin -I ~/.color/icc/i1.icc
	gnome-screensaver-command --exit
	export ARGYLL_IGNORE_XRANDR1_2=yes
	dispwin -L
	gnome-screensaver

attempts to set up ICC with a screen saver. The script stops gnome-screensaver, loads the calibration and restarts the gnome-screensaver. It's best to just disable the screen saver.

The quick way to check if you are affected by this:

dispwin -L -V (if OK)
gnome-screensaver-command -a
dispwin -L -V (if still OK you have solved the problem)

---

### Post by jazzgossen on 2009-10-08
Thanks for the guide.

Just a question: will this enable colour management on the X11 level, so that Gnome and everything else can look good on a wide-gamut monitor?

I'm considering buying a wide-gamut monitor, and I want to know before I buy it whether things other than the few available colour-managed apps will look right.

---

