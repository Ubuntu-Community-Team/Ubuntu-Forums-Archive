---
title: "ATI Dual Monitor - About to give up on Ubuntu"
date: 2008-11-04
forum: Hardware
---

### Post by joebodo on 2008-11-04
This is probably the third time I've tried to replace my MS desktop with Ubuntu. This latest version (8.10) is extremely close (if I could just get my VPNs configured). Unfortunately, I'm still having some basic problems with performance and with a dual monitor setup. I'm at the frustration level right now where I'm thinking maybe I should just wait for Jaunty.

I've spent too many hours now trying various configurations that have been suggested on many different sites. Any help with my issues would be appreciated.

**The issues**
1. Unable to run secondary monitor in any mode other than 1024x768
2. Bad performance viewing video with compiz enabled

**The setup**
ATI video card - SLI 1100
restricted/proprietary driver
1680x1050 viewsonic LCD (primary)
1600x1200 capable NEC analog monitor (secondary)
glxgears: 21510 frames in 5.0 seconds = 4301.845 FPS

(Please don't tell me to buy nvidia - ATI has 30% market share - Locking people into one hardware vendor seems to be very counter-intuitive to Ubuntu's philosophy)

**Xorg.conf**
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "TexturedVideo" "off"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by sandbox4us on 2008-12-01
I have the same problems.  My dual monitors were detected with a resolution of 1024x768, and I just couldnt get the CCC to recognize my monitors.  I tried and tried until my eyes went bleary... So I gave up.

On a whim I tried Kubuntu... I wasnt wedded to GNOME.  For whatever reason, the install went relatively smoothly and I had both my monitors working in no time.

---

### Post by markbuntu on 2008-12-02
Since you are using the fglrx driver, have you tried configuring the monitors in the Catalyst Control Center. It has and autodetect function that may fix your problem.

---

### Post by crypto2600 on 2009-04-26
AMDCCC detects both monitors, but only identifies ONE of them. And in the "Multi-Display" tab, the "Display Configuration" drop down is disabled and says "Unknown". Someone else asked this question and no one answered


Using ATI HD3200

---

### Post by jfanaian on 2009-05-11
I just started having this problem as well, but it only started happening after I switched to 64-bit Ubuntu. It worked just fine in the 32-bit version.

---

### Post by drubin on 2009-05-11
I am having the same [issue]("http://ubuntuforums.org/showthread.php?t=1155905") I think this is a ATI 64bit driver issue :( :(

---

