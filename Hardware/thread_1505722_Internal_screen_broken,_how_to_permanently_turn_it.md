---
title: "Internal screen broken, how to permanently turn it off"
date: 2010-06-09
forum: Hardware
---

### Post by jobzesage on 2010-06-09
Hi everyone !

I'm enjoying Ubuntu on my EeePC, sadly the other my laptop's screen broke down. I would like to turn my laptop in a "desktop" computer. When an external screen is plugged on the VGA port, I need to hit 4-5 times fn + F8 until my laptop's screen finally turns off and I get the proper resolution on my external screen (mirroring doesn't work as my desktop screen has a bigger resolution than the laptop).

So, every time I turn on the computer, or after it went to sleep, it goes back to the default mirroring mode.

I can also achieve the proper setting with the "Monitors" applet, but the changes doesn't last.

Any idea ???

Thanks :-) Jonathan

---

### Post by pytheas22 on 2010-06-09
You should be able to do this by editing your /etc/X11/xorg.conf file.  In modern versions of Ubuntu that file is usually empty by default, because the X server auto-configures itself on-the-fly.  However, I'm pretty sure that any values specified in xorg.conf will override X's auto-configured settings.

I'm not sure exactly what you need to put in to disable the internal monitor, but have a look at [this thread]("http://ubuntuforums.org/archive/index.php/t-186581.html").  According to that thread, the exact syntax may vary according to which video driver you're using, but on Intel chips, adding something like this to xorg.conf might work:
```

Section "Device"
Identifier "Default Video Card"
Driver "i810"
Option "MonitorLayout" "CRT,NONE"
```

With an ATI card, the syntax is apparently more like:
```

Section "Device"
Identifier "Default Video Card"
Driver "i810"
Option "ForceMonitors" "crt1, nolvds"
```

Hopefully this will help put you on the right track.  Editing xorg.conf is never a fun time (I'm glad the days of having to hack that file are long in the past!), but you can do a lot of powerful things with it once you understand how it works.

Also, keep in mind that you have to restart X (by logging out or running "sudo /etc/init.d/gdm restart") whenever you edit xorg.conf for changes to take effect.

---

### Post by jobzesage on 2010-06-09
Thanks for your hints !

I gave it a try, but the driver i810 wasn't installed on my Ubuntu. Then I wondered what driver it was actually using. Outside of X, I ran the command *X -configure* which created a xorg.conf file according to the automatic detection (if I understood it right).

I removed everything related to the input devices, and in the section Device, I added the option "MonitorLayout" (see the code enclosed). That didn't seemed to change anything... boring :-/

Any input on that ?

> Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Option	    "MonitorLayout" "CRT,NONE"
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 945GME Express Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by pytheas22 on 2010-06-09
i810 is the old driver for Intel video chips.  It hasn't been used since Ubuntu 8.04 or so, I think.  I should have mentioned that.  The new driver is named just "intel", and it's the one you're using.

I'd try adding the line:
```

Option "ForceMonitors" "Monitor0, nolvds"
```

in the "Device" section.  I'm not sure if this will work, but perhaps.

Also, [this thread]("http://ubuntuforums.org/showthread.php?t=528361") mentions possibly having an option in BIOS to turn the internal screen off.  I've never seen that on any of my laptops, but have you checked there?

---

### Post by jobzesage on 2010-06-10
Oh, that helps to understand a bit what's going on with these drivers, thanks. I'll try it out tomorrow, thank you for your help !

---

