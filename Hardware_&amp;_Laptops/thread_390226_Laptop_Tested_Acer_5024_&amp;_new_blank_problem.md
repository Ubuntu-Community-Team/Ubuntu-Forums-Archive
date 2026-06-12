---
title: "Laptop Tested: Acer 5024 &amp; new blank problem"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by bmhm on 2007-03-21
Hi every1

I just put my laptop into the wiki: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5024WLMi]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5024WLMi")

Now I got this problem:
My S3 (Suspend to ram) won't work anymore. Have NO Idea why. Here are the symptoms:
[LIST]
[*]Shuts down to S3 correctly
[*]When poweering on, nothing happens.
[*]Blank screen, no cursor, not even backlighting. Like being switched off, but it's not
[*]not even capslock-led working
[*]not even alt+print+b working
[/LIST]

I tried ALL options in:
[LIST]
[*]/etc/default/acpi-support
[*]/etc/default/fglrx
[/LIST]

Even worse: While connected to power plug, I can't shut it down by pressing power key for five seconds. It restarts. Won't happen, if I am running on batteries.

Now I discovered something new:
If I do "/etc/init.d/gdm stop" - same sitiuation as above, but I *can* restart gdm blindly, and everything will be fine again.

Funny thing about it: It DID work before. I tried to install hibernate packages... nothing.

I use ATI's 8.32.6 binary drivers. Why? Because newer drivers won't work. They make the screen stuck every 5 seconds, regardless of OpenGL or just Desktop working. Older drivers prevent switching to console (tty1).  So I downgraded - PROPERLY - to 8.32.6.

No Ideas anymore. Logs being attached. 

Any Ideas?

xorg.conf:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#-- cut ---

Section "ServerLayout"

#	InputDevice    "stylus" "SendCoreEvents"
#	InputDevice    "cursor" "SendCoreEvents"
#	InputDevice    "eraser" "SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
	Option	    "AIGLX" "false"
EndSection

# --- cut ---

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 67.0
	VertRefresh  30.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI RADEON X700"
	Driver      "fglrx"
	Option	    "DRI" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "XaaNoOffscreenPixmaps" "true"
	Option       "UseFastTLS" "2"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XaaNoOffscreenPixmaps" "true"
#	Option	    "EnablePrivateBackZ" "yes"
 	Option	    "DRI" "true"
	Option	    "UseFastTLS" "2"	
#	Option	    "NoMTRR"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X700"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

Any IDEAS???

---

### Post by bmhm on 2007-03-22
*bump*

---

