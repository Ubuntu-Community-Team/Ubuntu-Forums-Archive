---
title: "Help reconfiguring Xorg for installation"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by mike.sufc on 2009-04-02
Hi there, I have tried installing Ubuntu8.10 (and fedora10 I have the same problem with) but my monitor shows

"Input signal out of range" as soon as the graphical interface needs to be started

I have tried ```
sudo dpkg-reconfigure xserver-xorg
``` which takes me into the reconfigure programme, but just asks if I want something to do framebuffer, then tonnes of questions about my keyboard!

When I installed Mandriva, it went into a troubleshoot mode as soon as Xorg had a problem and asked what monitor, graphics adapter I had and what resolution/colour depth/frequency I wanted.  It then worked.  I expected a similar thing with Ubuntu but no?  Just loads of keyboard questions!

Is this what that reconfigure command should do?  And how would I reconfigure the resolution/frequency so it will start??

Any help appreciated,
Michael

---

### Post by sahabcse on 2009-04-02
Open the file and edit

Vim /etc/X11/xorg.conf

---

### Post by mike.sufc on 2009-04-02
ok...Well I did that and I dont know what to do! has different sections, then identifiers set as "configured device" or something similar.

I am not amazing with Linux, sorry.  I just want to make X work as I cant install without it!

And if I use the alternate CD, it installs but then I cant get into the login screen as I face the same problem.

Is it possible anybody could add a little bit of detail for a solution to getting xserver to actually start!?

---

### Post by mike.sufc on 2009-04-02
After some searching, it seems that modern Debian releases rely fully on auto-detection of hardware...But mine isn't being auto-detected properly...

I have a Hanns G monitor, an ATI HD3850 graphics card.  What can I do to make Xserver work!?

---

### Post by sahabcse on 2009-04-02
Hi

In which video card are you using. If you use nvidia means try vesa in your xorg.conf.



Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:3:0:0"
EndSection

---

### Post by mike.sufc on 2009-04-02
Thank you for your response

I use an ATI HD3850 :)

---

### Post by sahabcse on 2009-04-02
Hi

Follow below url, this may help

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by mike.sufc on 2009-04-02
This guide shows how to install the proprietry drivers and get them working better, but I can't even get anything working!

Oh well thank you for your time :) I appreciate it.  

I think Ubuntu just isn't for me at the moment if I cant even get past the installation (I did with previous versions though!!) I will try and get to grips with Mandriva.

---

### Post by sahabcse on 2009-04-02
Hi

Try ubuntu 8.04

---

### Post by humandraydel on 2009-04-02
I just started using Ubuntu about a week ago, and this was one of the first problems I had to solve.  This link helped me a lot:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

I have an ATI 4830 and a widescreen HP monitor so I had to edit xorg.conf to tell it the proper resolution and frequency.  Check that link for instructions on adding custom modelines and adding refresh rate to the xorg.conf file.  My xorg.conf looks like this:

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	HorizSync    58.0 - 68.0
	VertRefresh  55.0 - 65.0
	ModeLine     "1680x1050@60" 149.0 1680 1760 1944 2280 1050 1050 1052 1089 +hsync +vsync
	ModeLine     "1280x1024@60" 109.6 1280 1336 1472 1720 1024 1024 1026 1062 +hsync +vsync
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,lvds,tv,tmds1,crt2,tmds2,cv,tmds2i"
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
		Modes    "1680x1050@60" "1280x1024@60" "1280x1024@75"
	EndSubSection
EndSection

---

### Post by mike.sufc on 2009-04-02
That guide looks really good, thank you.  I will give this one last go i think tomorrow.  I must stop now and get on with some Uni work or I will get nothing done!!

I will post my results probably tomorrow!

---

