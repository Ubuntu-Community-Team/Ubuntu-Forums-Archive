---
title: "Dual head with ATI MOBILITY RADEON 900 on dell 600m laptop"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by Rocket2DMn on 2007-05-29
Hey guys,
I just installed Ubuntu the other day on my laptop with a dual boot with WinXP.  I'm not a complete *nix noob as I have used Unix and Fedora Core in the past, but I'm not terribly good at it.  
I've been searching forums on the internet for 2 days now and have not been able to get my external 15" monitor to run off the DVI port on my dell 600m docking station. 
hopefully relevant specs:
Dell 600m, 2ghz
ATI MOBILITY RADEON 9000, 64MB
built in LCD - 14"
external - 15" LCD (old gateway monitor) on DVI.  There is no VGA available on this monitor.

I think BigDesktop is the way to go, but I haven't managed to get anything showing on my second screen.
I have of course looked at 
[http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)
[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)
among other forums.

I have reset my xorg.conf file to the basic settings.
Perhaps video driver support for my card might be the issue, but I just don't know.
I appreciate any help you guys can give me.

---

### Post by Rocket2DMn on 2007-05-29
Anybody? please?

---

### Post by Rocket2DMn on 2007-06-03
OK, well for anybody who runs across this thread with the same question:
  It is no longer possible to do this with the ATI MOBILITY RADEON 9000 card.  ATI has cut support and although it worked before for people, something with the Feisty upgrade has resulted in the loss of dual head capacity.  Perhaps in the future somebody will write drivers to re-enable this, but until then, I suggest just using Beryl.

---

### Post by reckik on 2007-08-19
Hi, 

i had the same problem and didnt get a solution either. I did see though that ATI does have the old drivers for linux on their website. Myself i am a new to ubuntu so i cant give u much help their. 
BTW did u get the tv out function to work? Cause mine still doesnt work... 
here is a copy of my xorg.conf just in case ;)


Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

S
# Section "Device"
#	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
#	Driver		"radeon"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"radeon"
       Option          "XAANoOffscreenPixmaps"
        Option 		"AGPMode" "4"
        Option 		"AGPFastWrite" "true"
        Option 		"DisableGLXRootClipping" "true"
        Option 		"AddARGBGLXVisuals" "true"
        Option 		"AllowGLXWithComposite" "true"
        Option 		"EnablePageFlip" "true"
EndSection

#Section "Device"
#	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
#	Driver		"ati"
#       Option          "XAANoOffscreenPixmaps"
#        Option 		"AGPMode" "4"
#        Option 		"AGPFastWrite" "true"
#        Option 		"EnablePageFlip" "true"
#EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

### This part added###
Section "Extensions"
        Option "Composite" "True"
EndSection	


I did some editing myself and went back to the RADEON drivers instead of the FGLRX drivers. I constantly got the message that there was no screen detected.

---

### Post by Rocket2DMn on 2007-08-19
Hey, next time please don't post on old threads, just start a new one.
About the TV-OUT: The restricted drivers should already support this, but they just announced the other day that the open source drivers will be receiving tv-out capacity soon (if not already).  Story here: [http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

---

### Post by w4ett on 2007-08-19
One poster I was helping got their TV out going perfectly under Gutsy...apparently the:

[http://www.phoronix.com/scan.php?page=article&item=806&num=1](http://www.phoronix.com/scan.php?page=article&item=806&num=1)

procedures need xorg 7.3.....Feisty's xorg 7.2 results in incorrectly displayed colors.  BUT is is coming.....WooHoo!!  :)

---

