---
title: "laptop screen replacement shearing"
date: 2010-11-19
forum: Hardware
---

### Post by eddyojb on 2010-11-19
Hello,

I hope somebody can help me.


Specs:

Laptop: Vaio VGN-NS20Z
Dual boot OS: Ubuntu 10.10 and Vista


I'm currently experiencing issues with my new laptop screen (manufacturers replacement) that I've recently replaced due to breakage of the last one. I now get screen shearing where 3/4's of the screen will, at any random moment, go blurry and shear constantly unless I reset the computer.

The problem is that I'm convinced it's not hardware based but Ubuntu based, it doesn't seem to occur when I run Vista.

Is there anyone who can offer some help? I've had nothing but a lot of problems already with 10.10 Maverick, I spend countless hours trying to sort out all the niggly little problems but this problem is big and annoying as it can occur at any moment from 1 minute in to an hour of using my laptop, forcing me to reset and losing open stuff.

It is quite frustrating and unfortunately may drive me back to windows (GOD FORBID that I do but at least the screen works in it!)

Thanks in advance to anybody!

eddy

N.B I'm not an advanced Linux user so may need guidance if anyone's about to suggest probing and recording processes in terminal

---

### Post by tgalati4 on 2010-11-19
Plug in an external monitor and set it up in the Display control panel.  See if the tearing or other graphics weirdness shows up on the external display.  If so, then it's possible that your graphics chip is having problems.  Windows tends to better control the GPU temperatures.

I have a thinkpad t43 with an ati firegl graphics chip.  It runs several degrees hotter under Jaunty then under Windows XP.  I turned on the dynamic clock in xorg.conf and that lowers temperatures somewhat.  So I'm thinking it's a thermal issue rather than a display issue.  Add some gpu temperature widgets to your panel so you see what the temps are.

If the temperatures are under control, and you don't see tearing on the external display, then try the following:  Gently pinch the display bezel in the location where you see the tearing.  Sometimes the displays are defective or become damaged during installation or shipping.

---

### Post by eddyojb on 2010-11-21
Thanks for the tips.

What you said makes sense as I have an ATI graphics chip too and for a while I simply didn't install ATI's proprietary graphics driver and used Ubuntu's own, which seemed to work faster and effectively on my laptop. Unfortunately it obviously couldn't cope with the screen replacement so I installed ATI's driver and now it works fine, which infers that it better handles the gpu hence I don't get this funny effect anymore.

The only negative is a less aesthetically pleasing boot screen (random..) and slightly slower performance in some areas.

I'm no hardware expert but my laptop feels much hotter when running Ubuntu in general than in Windows, maybe this has got to do something with the gpu, which I guess indicates the need for better handling of graphics cards by Ubuntu.

Cheers

eddy

---

### Post by tgalati4 on 2010-11-26
You can turn on dynamic clocks in your xorg.conf to turn down the graphics clock dynamically.  You will have to search for exact setting, but for my ATI FireGL card the following works:


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1400 1050
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "Stereo" "off"
	Option "StereoSyncEnable" "1"
	Option "FSAAEnable" "no"
	Option "FSAAScale" "1"
	Option "FSAADisableGamma" "no"
	Option "FSAACustomizeMSPos" "no"
	Option "UseFastTLS" "0"
	Option "BlockSignalsOnLock" "on"
	Option "XAANoOffscreenPixmaps"
	Option "AccelMethod" "XAA"
#        Option "AccelDFS"    "true"

EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

---

