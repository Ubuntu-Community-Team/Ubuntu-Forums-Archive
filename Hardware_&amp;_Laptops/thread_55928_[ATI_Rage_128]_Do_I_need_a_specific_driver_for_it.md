---
title: "[ATI Rage 128] Do I need a specific driver for it?"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by ad1138 on 2005-08-10
Dows anybody know if my old ATI Rage 128 (32MB) needs a specific ATI driver (and, if so, where to find it) or if the default one that comes with Ubuntu is enough? Thanks in advance. :)

---

### Post by autocrosser on 2005-08-11
Straight from my old dual-card/dual-monitor xorg.conf----

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        Option      "VGAAccess"                 "true"
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "ForcePCIMode"       	# [<bool>]
        #Option     "CCEPIOMode"         	# [<bool>]
        #Option     "CCENoSecurity"      	# [<bool>]
        #Option     "CCEusecTimeout"     	# <i>
        #Option     "AGPMode"            	"4"
        #Option     "AGPSize"            	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        Option      "EnablePageFlip"     	"true"
        Option      "Display"            	"FP"
        Option      "PanelWidth"         	"1024"
        Option      "PanelHeight"        	"768"
        #Option     "ProgramFPRegs"      	"false"
        #Option     "VideoKey"           	# <i>
        #Option     "ShowCache"          	# [<bool>] 
        Option      "backingstore"              "true"
	Option     "AllowGLXWithComposite"     "true"                        
	#Option     "ShadowFB"          	"true"
	#Option     "fbdev"	                "/dev/fb1"
        Option      "UseFBDev"                  "true"
	BusID  	    "PCI:16:18:0"
	Identifier  "Rage 128"
	Driver      "r128"
        VendorName  "ATI Technologies Inc"
	BoardName   "ATI Rage 128GL RE"
EndSection

For more info on this driver--just man r128--edit it to work with your set-up (change PCI location-AGP-whatever you need--- :grin:

For more than this I would like to see your xorg.conf---but, with this & DRI enabled--you will get about as good as it gets---

---

### Post by ad1138 on 2005-08-11
Thank you for your help, Dean. :)

Here's my xorg.conf:
```

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107E"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Monitor		"PHILIPS 107E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Correct me if I'm wrong: the parameters I see in your xorg.conf are just "options" you've enabled, aren't they? If so (here comes the newbie question) how did you figure out which ones where the best for your video card?

Thanks again.

---

### Post by autocrosser on 2005-08-11
Well--most of the options were just trial&error--if the Xserver would not start, I would look at the error log & work with it--The r128 driver will work much better than the general ati driver--like I said, open a terminal & man r128 <return>---this will list all the current options for the card & what each one will do--

---

### Post by ad1138 on 2005-08-14
[QUOTE=autocrosser]Well--most of the options were just trial&error--if the Xserver would not start, I would look at the error log & work with it--The r128 driver will work much better than the general ati driver--like I said, open a terminal & man r128 <return>---this will list all the current options for the card & what each one will do--[/QUOTE]

I'll do it, thanks a lot for your help. :)

---

### Post by jks on 2005-08-14
Hi !
Does TVout work fine with r128 ?

---

### Post by ad1138 on 2005-08-14
[QUOTE=jks]Hi !
Does TVout work fine with r128 ?[/QUOTE]

Does it have tvout? God, I didn't even remember. :D
I tried to use it when I was running Windows but I got such a poor quality result that I just forgot it and never used it again. Maybe autocrosser uses it on Linux, hope he will help you.

---

### Post by jks on 2005-08-15
[QUOTE=ad1138]Does it have tvout? God, I didn't even remember. :D
I tried to use it when I was running Windows but I got such a poor quality result that I just forgot it and never used it again. Maybe autocrosser uses it on Linux, hope he will help you.[/QUOTE]

THX !  :smile: 

Unfortunately the driver r128 doesn't work perfectly with TVOUT...
I have nothing on screen (i.e black screen : Monitor and TV) when I start Ubuntu with my video cable connected. Message error on my monitor : "WARNING OUT OF RANGE".
When I start Ubuntu without my video cable (only DVI cable) : It works ! (but I can't use TVOUT... )

Any idea ?

I will try autocrosser but I think that the problem comes from Xorg.

Thanks.

---

### Post by autocrosser on 2005-08-15
Sorry--I don't have any info on the TV out issue--You can goto Sourceforge.org & search for ATI drivers--The Gato project is working on it, but I haven't looked at their info lately---I do know that the last time I looked, they had a "expermental" driver set---
 
 
Not much help, but that's what I've heard---

---

### Post by jks on 2005-08-16
[QUOTE=autocrosser]Sorry--I don't have any info on the TV out issue--You can goto Sourceforge.org & search for ATI drivers--The Gato project is working on it, but I haven't looked at their info lately---I do know that the last time I looked, they had a "expermental" driver set---
 
 
Not much help, but that's what I've heard---[/QUOTE]


THX !

---

### Post by morgengenuss on 2007-03-13
i got the tvout working using the vesa driver. only problem: on fullscreen the video-playback is not 100% smooth.

apart from that, everything seems fine. if anyone still needs assistance let me know.

and in case someone knows how to tweak xfce so that it will play videos smoothly let me know as well.

---

### Post by schruthensis on 2007-10-15
I also got this working using the generic Vesa drivers.    Basically i used some really basic / default-ish tv screen settings for my xorg.conf  file:


 Section "Device"
        Identifier      "Card0"
        Driver  "ATI Rage 128"
        Option  "AGP" "1"
        Option  "ConnectedMonitor" "TV"
        Option "TVStandard" "NTSC-M"
        #Option "AGPFastWrite" "yes"  #haven't tried this yet
        #Option "MonitorLayout" "NONE, CRT"   #haven't tried this either
 EndSection

 Section "Monitor"
        Identifier      "Monitor0"
        HorizSync    30.0 - 50.0
        VertRefresh  60
 EndSection

 Section "Screen"
        Identifier      "Screen0"
        Device          "Card0"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
 EndSection

---

