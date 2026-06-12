---
title: "1280x1024 resolution on laptop + external monitor"
date: 2006-08-16
forum: Hardware &amp; Laptops
---

### Post by jorganizam on 2006-08-16
Hi,

I installed Ubuntu 6.06 few days ago on my laptop (Compaq nc6120 - graphic controler: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller)

It works fine when I use just laptop. But when I connect it to docking station which is connected to 19" Dell 1907FP LCD, I would like to use higher resolution 1280x1024. Applet System -> Preferences -> Screen Resolution doesnt offer any resolution larger than 1024x768.

I looked at several similar posts on ubuntu forums but nothing worked. In xorg.conf I inserted Mode "1280x1024". I also tried dpkg-reconfigure xserver-xorg, I selected the resolution but it didn't show in the applet. I tryed to enter horizontal and vartical resolution in xorg.conf but it didn't work either etc.

Does anybody have an idea what to do? Thanks :-)

Orginal xorg.conf without 1280x1024 Mode is below

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbLayout"	"hr"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
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

---

### Post by wieman01 on 2006-08-16
Here is a sample "xorg.conf" that you can use & adjust according to your needs & hardware. I'll try this out soon as well. 

[http://www.ubuntuforums.org/showthread.php?t=234102]("http://www.ubuntuforums.org/showthread.php?t=234102")

To cut a long story short, you need to configure a second screen using "xorg.conf" and insert this line:
> Screen "ExtScr" RightOf "IntScr"
But see for yourself.

---

### Post by jorganizam on 2006-08-17
I tryed what you recomended but it didn't work. During X initialization something like this is reported in xorg.0.log: Failed to initalize second screen beacause initialization of the first failed, and no screens found.

Here is my xorg.conf.

```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbLayout"	"hr"
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
	Identifier	"IntDevice"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ExtDevice"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"IntLCD"
	Option		"DPMS"
	HorizSync	43.89-48.51
	VertRefresh	60
EndSection

Section "Monitor"
	Identifier	"ExtLCD"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"IntScreen"
	Device		"IntDevice"
	Monitor		"IntLCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"ExtScreen"
	Device		"ExtDevice"
	Monitor		"ExtLCD"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dualhead"
	Screen		"IntScreen"
	Screen		"ExtScreen" RightOf "IntScreen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection

```

---

### Post by wieman01 on 2006-08-17
Ok, I have to admit I have not tried this yet, but as soon as I do (very soon) I'll let you know what my solution looks like...

---

### Post by jorganizam on 2006-08-18
I solved my problem (took me 3 days ](*,) )

The problem was that that X took the largest supported resolution that both monitors can handle and that was 1024x768. So when I turned of laptop monitor (Fn + F4) and restarted X (ctrl + alt + backspace). The resolution 1280x1024 appeared in "Screen Resolution" applet.

---

### Post by wieman01 on 2006-08-18
Excellent, jorganizam. I'll use this for my own laptop. Thanks for posting this.

---

### Post by Nivriki on 2006-09-07
Hey thanks jorganizam, that tip helped me set the resolution on my Dell monitor :D

---

### Post by wieman01 on 2006-09-09
Hello Jorganizam, 

I may need your help & advice. My configuration looks like this:
[HTML]Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Option       	"LeftEdge"        	"120"
    	Option       	"RightEdge"        	"830"
    	Option       	"TopEdge"        	"120"
   	Option      	"BottomEdge"        	"650"
  	Option     	"FingerLow"        	"14"
  	Option      	"FingerHigh"        	"15"
  	Option      	"MaxTapTime"        	"180"
  	Option  	"MaxTapMove"        	"110"
    	Option    	"EmulateMidButtonTime"  "75"
   	Option   	"VertScrollDelta"    	"20"
   	Option     	"HorizScrollDelta"    	"20"
  	# orig = 0.25
	Option    	"MinSpeed"        	"0.7"
	# orig = 0.75
  	Option    	"MaxSpeed"        	"0.9"
	# orig = 0.015
  	Option     	"AccelFactor"        	"0.035"
	# orig = 200
  	Option     	"EdgeMotionMinSpeed"    "350"
	# orig = 200
   	Option      	"EdgeMotionMaxSpeed"    "350"
  	Option    	"UpDownScrolling"    	"1"
  	Option    	"LeftRightScrolling"    "1"
   	Option     	"CircularScrolling"  	"1"
  	Option     	"CircScrollDelta"    	"0.1"
  	Option     	"CircScrollTrigger"    	"2"
EndSection

Section "Device"
	Identifier	"Internal Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 		0
EndSection

Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	HorizSync	30-60
	VertRefresh	50-75
	Option		"DPMS"
	Modeline    	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76 
        ModeLine 	"1024x768" 78.75 1024 1040 1136 1312  768  769  772  800 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection	
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dualhead"
	Screen		"Internal Screen"
	Screen		"External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option  "Composite" "Enable"
#EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection
[/HTML]
However, I get the following error message while the system hangs right before the log-on screen:
> (EE) I810(0): You must have a MonitorLayout defined for use in a DualHead or Clone setup.
(EE) I810(1): Failed to setup second head due to primary head failure.
(EE) Screen(s) found, but none have a usable configuration.
Any idea what's wrong?

---

### Post by wieman01 on 2006-09-09
Again answering my own question... This is the right file which works for me. Now enjoying movies on my external projector. :-)
[HTML]Section "Device"
	Identifier	"Internal Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"	"CRT,LFP"
	Screen 		0
EndSection

Section "Device"
        Identifier	"External Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout" "CRT,LFP"
	Option		"TVOutFormat" "Composite" 
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Internal Monitor"
	HorizSync	30-60
	VertRefresh	50-75
	Option		"DPMS"
	Modeline    	"1280x768" 80.14 1280 1344 1480 1680 768 769 772 795
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option  	"DPMS"
        HorizSync 	30 - 85
        VertRefresh 	56 - 76
EndSection

Section "Screen"
	Identifier	"Internal Screen"
	Device		"Internal Device"
	Monitor		"Internal Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection	
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "External Device"
        Monitor         "External Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Dual Head"
	Screen		"Internal Screen"
	Screen		"External Screen" RightOf "Internal Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#	Option  "Composite" "Enable"
#EndSection

Section "ServerFlags"
       Option		"Xinerama" "true"
EndSection
[/HTML]

I had to add this line: 
> Option		"MonitorLayout" "CRT,LFP"
Plus the "DefaultDepth" of both screens must be the same.

If I want to turn it off, I simply comment out this line & restart the x-server:
> #Screen		"External Screen" RightOf "Internal Screen"

---

### Post by shaviro on 2006-09-12
I tried this, including enabling Xinerama, and it seems to work -- but the result is that my workspace is extended to the second (external) monitor, whereas what I would like to do is for the external monitor to mirror my laptop screen, rather than extending it. Is there a way to do this? can I set up the external screen to be something other than "RightOf" the primary screen?

Also -- to turn the external screen on and off, I have to -- as is mentioned above -- comment out and restore a line in xorg.conf. Is there any way to do this more directly, e.g. by a function key or by a single line (similar to i855crt) in the terminal?

thanks

---

### Post by wieman01 on 2006-09-12
Got your point... If you want to mirror your laptop screen then you have to add 2 "screen" lines under "ServerLayout" which will look like this (there are other options as well... check it out on the web):
> # overlapping screens
Screen          0 "internal screen virtual"
Screen          1 "external screen" Relative "internal screen virtual" 0 1
I did that but the problem again is Sony's widescreen. In all likelyhood your external screen's visible rectangle and your laptop's won't be congruent, therefore maximized programs on your laptop screen won't maximize on your external display, occupying only a fraction of it. It's odd but I could not figure out how to tackle this one.

As for your second question, no, I have not found a way to enable the external device by a click of a button. My solution is to mess around with the xorg.conf file. I know this is not ideal but in my case I don't mind since I only do so when I want to watch movies using my projector.

---

### Post by shaviro on 2006-09-12
I tried adding the lines to xorg.conf, but the result was that X-server wouldn't load, I had to remove them again. 

Any other suggestions?

thanks...

---

### Post by wieman01 on 2006-09-13
My mistake... These lines must match your screens of course. Try this:
> Screen 0 "Default Screen"
Screen 1 "External Screen" Relative "Default Screen" 0 1
Does this make the difference?

---

### Post by shaviro on 2006-09-13
Yes, now everything works.

thanks.

---

### Post by wieman01 on 2006-09-13
Great! Could you tell me if full-screen on the second device is a problem? If you don't mind could you upload an screenshot of each desktop when running them im parallel? I am just curious...

---

### Post by shaviro on 2006-09-14
>Great! Could you tell me if full-screen on the second device is a problem? >If you don't mind could you upload an screenshot of each desktop when >running them im parallel? I am just curious...

I don't have any screenshots. The second device is a video projector. I am a teacher, and I need for my class to be able to see the presentations I have made and that I have on my laptop. I have both the laptop and the projector set to 1048x768; I have not tried to do this using the extra-wide screen capabilities of the Vaio.

---

