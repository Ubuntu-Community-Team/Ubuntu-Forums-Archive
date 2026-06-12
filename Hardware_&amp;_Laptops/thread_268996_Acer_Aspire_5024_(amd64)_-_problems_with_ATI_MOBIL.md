---
title: "Acer Aspire 5024 (amd64) - problems with ATI MOBILITY RADEON X700 PCIE"
date: 2006-10-01
forum: Hardware &amp; Laptops
---

### Post by pitrowech on 2006-10-01
Hi guys, i've been trying to get my videocard 3d support working for almost 6 hours without any results =(((((((((.

I followed this guide precisely:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually")

2d - acceleration seems to work fine.

Here's the error log:
```

root@spooky-house:/usr/bin# cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux spooky-house 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): Hardware has already been locked.
root@spooky-house:/usr/bin# cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) fglrx(0): Failed to open DRM connection
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(WW) fglrx(0): Option "(null)" is not used


```


xorg.conf:
```

Section "ServerLayout"

#	Screen      0  "aticonfig-Screen[0]" 0 0
	Identifier     "Default Layout"
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"

#	Load  "GLcore"
#	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us,ru"
	Option	    "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"

#	ModeLine     "1280x800@60" 83.9 1280 1312 1624 1656 800 816 824 841
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"

#	Identifier   "aticonfig-Monitor[0]"
#	Option	    "VendorName" "ATI Proprietary Driver"
#	Option	    "ModelName" "Generic Autodetecting Monitor"
#	Option	    "DPMS" "true"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
 #"ati" #"vesa" #"fglrx" #"ati"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Driver      "radeon"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"

#	Identifier  "aticonfig-Device[0]"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"

#		Modes    "1024x768" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"

#	Identifier "aticonfig-Screen[0]"
#	Device     "aticonfig-Device[0]"
#	Monitor    "aticonfig-Monitor[0]"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

crossposted:
laptop support
video & sound

---

### Post by jrohde on 2006-10-01
Hi Pitrowech,

Have you tried using Ubuntu 32Bit? I have given up on the 64 bit edition because of driver problems and lack of important Firefox extensions. And I can't see any difference in performance anyway.

This line is weird:

Current Operating System: Linux spooky-house 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64

What is "spooky-house"?

What version of Ubuntu are you using?

I have an Acer Ferrari 4000 with a ATI Radeon X700 that runs 3D fine.

Jakob

---

### Post by pitrowech on 2006-10-01
Hello, Jakob.

"spooky-house" is actually hostname of my computer.
Currently i'm using Ubuntu 6.06 LTS - Dapper Drake, ugraded from 5.10 installation.

I know, that installing 32-bit OS will be easiest solution, but this is a question of principles =)

Thanks for your reply.

---

