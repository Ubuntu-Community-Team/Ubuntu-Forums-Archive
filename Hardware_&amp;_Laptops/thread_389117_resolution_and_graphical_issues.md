---
title: "resolution and graphical issues"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by dusdus on 2007-03-20
greetings,

My laptop, a Toshiba Satellite pro 6100 is a second hand one and I love 'm :)
Finally I got the Nvidia GeForce2 420 Go up and running, using the Envy-script to install the correct driver.
After installing the nvidia driver I got sounds, the system up and running, though a black screens.
It seemed I needed to add something to my xorg.conf:
	Option		"UseDisplayDevice"	"DFP"

and indeed, that did the trick.

Problem now is, I can't change the resolution and I have some frustrating black stripe to the right of my screen; which is about 1.5 inch wide. 
Chosing System --> Preferences --> Screen Resolution I can only chose 800x600 and 640x480. The refresh rate can be 50 or 52.

Before installing the nvidia drivers the resolution was 1024x768, and if I remember correctly the refresh rate was 60.

So I tried and it seems a lot of people have this problem. 
As I dont know the actual sync and refresh rates, I had to try some generic ones:
```

Section "Device"
	Identifier	"NVIDIA GeForce4 420 Go"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"UseDisplayDevice"	"DFP"
	Option "IgnoreEDID" "1"
	Option "UseEdidFreqs" "0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	33-75
	VertRefresh	55-70
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

```

As you can see I've been experimenting a little with the lines IgnoreEDID etc, trust me also without those lines it simply wont work.

```

ection "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce4 420 Go"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I've read and done a lot of how-to's concerning this problem and I have this feeling I'm overlooking some simple thingy...

who can help me look?

---

### Post by dusdus on 2007-03-20
So now I've followed the instruction on this website:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

7) If you own a GeForce4 420/440 Go or a GeForce4 MX 440 you should follow these steps:

etc...

Now it looks like I have a better/ the correct resolution, though all fit in a smaller part of the screen.
So now the screen which I can see ubuntu in is surrounded with black bars!
It looks sharper though :P

and still, the application: System -> Preferences -> Screen Resolution says: 800x600.

So anyone has some bright ideas?!

---

### Post by adipl on 2007-03-20
try the following:

```
Section "Device"
	Identifier	"NVIDIA GeForce4 420 Go"
	Driver		"nvidia"	
	BusID		"PCI:1:0:0"	
	Option		"NvAGP"		"1"	
	Option		"NoLogo"
	#without the following, a black stripe appears in the right of the screen
	Option		"ExactModeTimingsDVI"	"true"
	Option		"ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"		
EndSection
```

---

### Post by dusdus on 2007-03-21
> **adipl said:**
> try the following:

```
Section "Device"
	Identifier	"NVIDIA GeForce4 420 Go"
	Driver		"nvidia"	
	BusID		"PCI:1:0:0"	
	Option		"NvAGP"		"1"	
	Option		"NoLogo"
	#without the following, a black stripe appears in the right of the screen
	Option		"ExactModeTimingsDVI"	"true"
	Option		"ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"		
EndSection
```

Thanks for your reply.
At the moment I'm staring at a small window in my screen which resembles a resolution of 1024x768, but is very small. It has black borders all around it. Ubuntu says its 800x600.

btw, as soon as I remove the line "UseDisplayDevice"  "DFP", I'll get e completely black screen.

---

### Post by dusdus on 2007-03-21
I've tried a lot of options now, like including Modeline specifications, and I've tried some different Options in the Device and Screen section.

Still I'm having the same problem.
Here is my complete xorg.conf, maybe it'll make some more clear:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce4 420 Go"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"UseDisplayDevice"	"DFP"
#	Option "UseEDID" "False"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	33-95
	VertRefresh	55-160
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce4 420 Go"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768_60" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768_60" "800x600" "640x480"
	EndSubSection
	
Option "ExactModeTimingsDVI" 
Option "UseEdidDpi" "FALSE" 
Option "ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

does anyone have an idea?

---

### Post by adipl on 2007-03-21
ok. Try one completely new and different approach. This approach is compiled from:

[http://www.nvnews.net/vbulletin/showthread.php?t=80317](http://www.nvnews.net/vbulletin/showthread.php?t=80317)

It basically boils to get a valid VESA EDID structure and then use that one instead of the buggy one in your monitor. You retrieve a valid EDID (from e.g., similar maching running xp) with a freeware program called "Phoenix EDID Designer" ( [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441) ). Then you export it in raw  format and finally use it in linux by adding in your xorg.conf the following:


```
	Option		"UseDisplayDevice"		"DFP-0"
	Option		"CustomEDID"			"DFP-0:/[COLOR="Red"]where/you/saveit/_justafilename[/COLOR].raw"
```

Now, you should remove the extra options that I mentioned in my earlier post. Also, with this method you dont need to add anything more (i.e., you dont need to add extra parameters to the nvidia module).

There is also the possibility to fix the one in your monitor in a very similar way: 
[http://www.nvnews.net/vbulletin/showthread.php?t=81635](http://www.nvnews.net/vbulletin/showthread.php?t=81635)

Tell me if it helps.

---

### Post by dusdus on 2007-03-21
thanks for the reply.
I've seen a similar approach wich was regaring hex-editing the EDID-file, which was a bridge too far for me :P

I'm going to try this now

*reboots his laptop to windows*

---

### Post by dusdus on 2007-03-21
> **adipl said:**
> ok. Try one completely new and different approach. This approach is compiled from:

[http://www.nvnews.net/vbulletin/showthread.php?t=80317](http://www.nvnews.net/vbulletin/showthread.php?t=80317)

It basically boils to get a valid VESA EDID structure and then use that one instead of the buggy one in your monitor. You retrieve a valid EDID (from e.g., similar maching running xp) with a freeware program called "Phoenix EDID Designer" ( [http://www.tucows.com/preview/329441](http://www.tucows.com/preview/329441) ). Then you export it in raw  format and finally use it in linux by adding in your xorg.conf the following:


```
	Option		"UseDisplayDevice"		"DFP-0"
	Option		"CustomEDID"			"DFP-0:/[COLOR="Red"]where/you/saveit/_justafilename[/COLOR].raw"
```

Now, you should remove the extra options that I mentioned in my earlier post. Also, with this method you dont need to add anything more (i.e., you dont need to add extra parameters to the nvidia module).

There is also the possibility to fix the one in your monitor in a very similar way: 
[http://www.nvnews.net/vbulletin/showthread.php?t=81635](http://www.nvnews.net/vbulletin/showthread.php?t=81635)

Tell me if it helps.

Yes! It works! Like a charm! Thank you soooo much! It was pretty much easy too :D

btw, the windows prog seems to work fine with wine :)

I really wonder how you found these forumthreads, I though I was doing pretty well in searching the inet :P

---

### Post by adipl on 2007-03-21
Glad to know that it worked for you too. 
Well I used the power of google. :lolflag: :lolflag: :lolflag:

---

