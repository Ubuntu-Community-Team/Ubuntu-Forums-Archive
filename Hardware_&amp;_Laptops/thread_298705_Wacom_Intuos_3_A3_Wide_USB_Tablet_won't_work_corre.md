---
title: "Wacom Intuos 3 A3 Wide USB Tablet won't work correctly"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by darkmaster on 2006-11-13
Hi all. The problem is as follows. I have an Acer Aspire 5510WLMI laptop and I installed Ubuntu Edgy Eft. 

I need to use my Wacom Intuos 3 A3 Wide Tablet on this PC. When I plugged in the USB for the first time, the following happened: 
1) The tablet led got turned on
2) If I move the pen ON the Tablet, the mouse pointer moves but it is not centered. I can reach only a part of the screen and I have to touch the tablet with the pen to move the pointer! In Mac OSX the pointer moves even if the pen is at a certain distance from the tablet, wich is the correct way of using it. And everything is centered too. In Ubuntu all this does not happen. It seems that depending on the pressure I use, the tablet interprets my movement as a click or as a simple movement of the pen. 
3) In Gim, if I try to use the extended imput.... it says there's no extended device. 

I then found this link:
[http://www.ubuntuforums.org/showthread.php?t=25151&page=3]("http://www.ubuntuforums.org/showthread.php?t=25151&page=3")
Before following the thread, my xorg was this:

> Section "Files"
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
	Option		"XkbLayout"	"it"
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
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout" "LVDS, auto"
#	Option 		"RenderAccel"    "1"
	Option 		"NoRenderExtension"   "0"
	Option 		"XAANoOffscreenPixmaps" "1"
	Option 		"AllowGLXWithComposite" "1"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor		"Generic Monitor"
	Option 		"AddARGBGLXVisuals" "1"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option		"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
  	Option     	"Composite"  "Enable"
  	Option     	"RENDER"    "true"
  	Option     	"DAMAGE"     "true"
EndSection

At this point I read all the thread and saw about the wacom-tools. I installed them before continuing. I then also tested the imput device to find out that the device on wich my usb wacom tablet works is numer 3. I also tested the wacom one after the reboot and it pointed correctly to my wacom tablet since if I used the pen the screen on the console got all messed up. As it should :)
I Noticed that moving the pen NEAR to the tablet caused the same messing up, so, the computer notices that there's an imput even if I don't actually touch the tablet with the pen. 

After the work, my Xorg looked like this:

> Section "Files"
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
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice" 
#Questo ?® il Mouse USB. Ho scoperto che ?® mouse2. Se non funge pi?? il touchpad, lo devo cambiare in "mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "cursor"
  Option        "Mode"          "relative"
  Option        "USB"           "on"                  #USB ONLY
  Option        "ForceDevice"   "ISDV4"               #Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/ttyS0"          #SERIAL ONLY
  Option        "Device"        "/dev/input/wacom"   
  Option        "Type"          "pad"
  Option        "USB"           "on"                  #USB ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"MonitorLayout" "LVDS, auto"
#	Option 		"RenderAccel"    "1"
	Option 		"NoRenderExtension"   "0"
	Option 		"XAANoOffscreenPixmaps" "1"
	Option 		"AllowGLXWithComposite" "1"

EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor		"Generic Monitor"
	Option 		"AddARGBGLXVisuals" "1"
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice    "pad"
	Option		"AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
  	Option     	"Composite"  "Enable"
  	Option     	"RENDER"    "true"
  	Option     	"DAMAGE"     "true"
EndSection

I then rebooted again. There was absolutely no difference from the first time I tryed and use the tablet. It is not centered, I have to press the pen on the tablet to make the pointer move and the Gimp says I have no extended device.

Ok now, since a lot of people around the forums seem to have had the Tablet working, what am I doing wrong? What's the big missing point? There must be something wrong indeed but I cannot figure it out. 

Please help me, I'm not a complete newbye but a step by step is better 'cause I tend to misunderstand when people tryes to make the explanation quicker.

I posted every detail and thing I tought could help you understanding my problem. If you need some more info, please, ask me.

---

### Post by Ryupower on 2006-11-13
Hey, got the same problem with the graphire tablet on Dapper. 
My thread is basicly about the same thing, and has more replies ( so far ):

[http://ubuntuforums.org/showthread.php?t=297684](http://ubuntuforums.org/showthread.php?t=297684)

---

### Post by darkmaster on 2006-11-13
I already read your post, there's no usefull answer.
It is not that similar to mine after all. My X server never gets crashed, it's a different problem and plus I've got an Intuos 3 and not a graphire wich, I believe, is an important difference.

---

### Post by Ryupower on 2006-11-13
So did you look at the link I put in the thread?
It was about how to configure your Tablet for pressure sensitivity.
Prob what you're looking for ( the cursor moving without needing to press on the board I think would be considered pressure sensitivity )

Did you configure it as they said in this thread?

[http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom](http://ubuntuforums.org/showthread.php?t=25151&highlight=wacom)

Maybe it will work for you.

Good luck

---

### Post by darkmaster on 2006-11-13
Ok, Thanks. Just look at my post and you'll see I posted the same link :) followed it and didn't work at all. Everything was identical to thge beginning. Read the first part of my post again... and the tablet isn't still centered...

---

### Post by darkmaster on 2006-11-16
Nobody answered to my topic but I solved the problem by myself.
Basically, to make the wacom tablet work you have to comment the line reguarding SERIAL ONLY, and that's all. Restart your PC and the tablet will work. To make it straight clear, my Xorg now looks like that (Only the part interested):


> Section "InputDevice"
Identifier	"Configured Mouse"
Driver	 "mouse"
Option	 "CorePointer"
Option	 "Device"	 "/dev/input/mice" 
Option	 "Protocol"	 "ExplorerPS/2"
Option	 "ZAxisMapping"	 "4 5"
Option	 "Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/ttyS0" #SERIAL ONLY
Option "Device" "/dev/input/wacom" 
Option "Type" "stylus"
Option "USB" "on" #USB ONLY
Option "ForceDevice" "ISDV4" #Tablet PC ONLY
Option "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/ttyS0" #SERIAL ONLY
Option "Device" "/dev/input/wacom" 
Option "Type" "eraser"
Option "USB" "on" #USB ONLY
Option "ForceDevice" "ISDV4" #Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/ttyS0" #SERIAL ONLY
Option "Device" "/dev/input/wacom" 
Option "Type" "cursor"
Option "Mode" "relative"
Option "USB" "on" #USB ONLY
Option "ForceDevice" "ISDV4" #Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "pad"
Option "Device" "/dev/ttyS0" #SERIAL ONLY
Option "Device" "/dev/input/wacom" 
Option "Type" "pad"
Option "USB" "on" #USB ONLY
EndSection

and don't forget this too:

> Section "ServerLayout"
Identifier	"Default Layout"
Screen	 "Default Screen"
InputDevice	"Generic Keyboard"
InputDevice	"Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "pad"
Option	 "AIGLX" "true"
EndSection


Hope it's going to help you too.

---

### Post by Sir Frederic on 2007-04-01
thanks for the info- i am thinking of buying one of those.

---

### Post by darkmaster on 2007-04-02
> **Sir Frederic said:**
> thanks for the info- i am thinking of buying one of those.

Well, if a feedback can help you, I have to say that tablet really changed my life :) It is really something and The Gimp works very well with it. If you buy one, don't forget to try out Gogh (For Linux, Opensource) and Artrage (For Windows, works under Linux very well with wine or crossover) wich is a freeware for the basic version and some money for the professional one. Byeeee!

---

