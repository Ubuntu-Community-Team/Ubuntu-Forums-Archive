---
title: "Is extended display possible with Inspiron 6000"
date: 2008-05-09
forum: Hardware
---

### Post by botbanky on 2008-05-09
So I just migrated from Windows to Ubuntu 8.04 and everything was going smoothly.  I then went to extend my desktop display from my laptop monitor to my 20" dell monitor, something I do on Windows all the time for work.  However, I can't seem to find any way to make this work.  When I go to the System > Preferences > Screen Resolution area I uncheck "clone screens" and move the two monitor representations side by side, hit apply, and then nothing happens-- just the same cloned display appears on both monitors.  When I close out the Screen Resolution box and reopen, the  "clone screens" box is checked again-- like my changes never happened.   

Does anyone know a solution for this?  My video card is some generic dell garbage: Intel Mobile 915GM/GMS/910GML Express Graphics Controller.  Am I out of luck thanks to not having the NVIDIA card I've seen referenced on this forum for extended desktop control?  I really hope not or else I'll have to dual boot into windows whenever I need to do real work work.... ugh.

Thanks,
Scott

---

### Post by fsgpr on 2008-08-05
The following worked for me on a laptop with Intel Video (though mine is a bit newer):

Go to a Terminal and enter:

   [INDENT] sudo gedit /etc/X11/xorg.conf[/INDENT]

Scroll down to Section "Screen" and add a Display subsection so you get something like the following:

[INDENT]Section "Screen"
[INDENT]Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
[INDENT]		Virtual 2560 1024[/INDENT]
	EndSubSection
[/INDENT]EndSection
[/INDENT]
The numbers after Virtual should represent how many pixels wide and tall you want your two monitors combined.  After saving this change, I was able to use the Screen Resolution utility to extend my desktop after a reboot.

---

### Post by unixkids on 2009-02-03
display problems with [inspiron 6000]("http://www.sales-battery.com/laptop-batteries/dell-inspiron-6000.htm")?

I also the same problem, ubuntu is great but it is very hard to ajust for my LCD monitor and PC monitor. I have tried many times but failed.

---

