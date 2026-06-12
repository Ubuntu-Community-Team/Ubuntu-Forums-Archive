---
title: "ATI Video card upgrade ends in X casualty... :/"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by m0unds on 2005-08-11
Hi everyone,

I was running an ATI Radeon 9800 Pro previously, and have upgraded my video subsystem. I'm thinking that the bus location might have changed, because when X tries to start, utilizing the fglrx driver, it crashes. I loaded my default x config and am using the machine to type this message.

The card is AGP, so I don't think there should be any issues with supporting it..is there something I should have done prior to the card upgrade? What can I do to rectify this situation?

Here's the broken XORG config:

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
	Load 	"GLcore"
#load extmod but moit dga extension
	SubSection "extmod"
		Option "omit xfree86-dga"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon x850XT Platinum Edition (R480)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

	#if X doesnt wanna use my res uncomment this
	#Option "NoDDC"
# === Video Overlay for the Xv extension ===
  Option "VideoOverlay" "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
  Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
  Option "UseInternalAGPGART" "no"

EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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


and the error at startup:

(II) Primary Device is: PCI 01:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by autocrosser on 2005-08-11
Try to change the device to the reported  PCI 01:00:0  instead of your PCI 1:0:0 and see if you get Xserver

Section "Device"
Identifier "ATI Technologies, Inc. Radeon x850XT Platinum Edition (R480)"
Driver "fglrx"
BusID "PCI:1:0:0" <--- to "PCI:01:00:0"

Also--It looks like this is a dual-head card & Xorg is looking for the device section for the second head?? 
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

In any case try the PCI id mod first & post your results----

---

### Post by m0unds on 2005-08-11
[QUOTE=autocrosser]Try to change the device to the reported  PCI 01:00:0  instead of your PCI 1:0:0 and see if you get Xserver

Section "Device"
Identifier "ATI Technologies, Inc. Radeon x850XT Platinum Edition (R480)"
Driver "fglrx"
BusID "PCI:1:0:0" <--- to "PCI:01:00:0"

Also--It looks like this is a dual-head card & Xorg is looking for the device section for the second head?? 
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found

In any case try the PCI id mod first & post your results----[/QUOTE]
 (II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "extmod"
(II) Reloading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension DPMS
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "fglrx"
(II) Loading /usr/X11R6/lib/modules/drivers/fglrx_drv.o
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 4.3.99.902, module version = 8.8.25
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) ATI Radeon/FireGL: The following chipsets are supported:
	FireGL - (RV250 4964), FireGL - (RV250 4965),
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY FireGL - (M9 4C65),
	MOBILITY RADEON 9000 (M9 4C66), RADEON 9000 PRO (D9 4C67),
	RADEON 9250 (RV280 5960), RADEON 9200 (RV280 5961),
	RADEON 9200 SE (RV280 5964), MOBILITY RADEON 9200 (M9+ 5C61),
	MOBILITY RADEON 9200 (M9+ 5C63), FireGL 8800 (R200 5148),
	RADEON 8500 (R200 514C), RADEON 9100 (R200 514D),
	RADEON - (R200 5154), RADEON - (R200 5155),
	RADEON 8500 AIW (R200 4242), RADEON 9600 (RV350 4150),
	RADEON 9600 SE (RV350 4151), RADEON 9600 PRO (RV360 4152),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50), RADEON 9500 (R300 4144),
	RADEON - (R300 4145), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	FireGL - (R350 414B), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), FireGL - (RV350 4155), FireGL - (RV350 4156),
	FireGL - (RV350 4157), RADEON 9800 PRO (R350 4E48),
	RADEON 9800 (R350 4E49), RADEON 9800 XT (R360 4E4A),
	FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON - (RV370 5B61), RADEON X600 (RV380 5B62),
	RADEON - (RV370 5B63), FireGL V3100 (RV370 5B64),
	FireGL - (RV370 5B66), FireGL - (RV370 5B67),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON - (M22 5461),
	MOBILITY RADEON - (M22 5462), MOBILITY RADEON - (M22 5463),
	MOBILITY FireGL V3100 (M22 5464), MOBILITY FireGL - (M22 5465),
	MOBILITY FireGL - (M22 5466), MOBILITY FireGL - (M22 5467),
	RADEON X600 (RV380 3E50), RADEON - (RV380 3E51),
	RADEON - (RV380 3E52), RADEON - (RV380 3E53),
	FireGL V3200 (RV380 3E54), FireGL - (RV380 3E55),
	FireGL - (RV380 3E56), FireGL - (RV380 3E57),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON - (M24 3151),
	MOBILITY RADEON X300 (M22 3152), MOBILITY RADEON - (M24 3153),
	MOBILITY FireGL V3200* (M24 3154), MOBILITY FireGL -* (M24 3155),
	MOBILITY FireGL -* (M24 3156), MOBILITY FireGL -* (M24 3157),
	RADEON X800 (R420 4A48), RADEON X800 PRO (R420 4A49),
	RADEON X800 SE (R420 4A4A), RADEON X800 XT (R420 4A4B),
	RADEON X800 (R420 4A4C), FireGL X3-256 (R420 4A4D),
	MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 XT Platinum Edition (R420 4A50), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 SE (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	FireGL -* (R423 5552), MOBILITY RADEON X800 XT (M28 5D48),
	MOBILITY FireGL V5100* (M28 5D49), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700 (RV410 5E4F),
	RADEON - (RV410 5E52), RADEON - (RV410 5E53), RADEON - (RV410 5E55),
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835)
(II) Primary Device is: PCI 01:00:0
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found


that's after i changed the entry as suggested.

---

### Post by autocrosser on 2005-08-11
Take a look at the man radeon (in a term)---I'd try to say that there are no screens attached to that port--

First try (if the card is dual-port) the monitor in the other port--

I'm also leaning towards changing the original device to the PCI:1:0:1 & just try that before adding a second device section--

Also, try copying your device section & change the bus address to the PCI:1:0:1--(use two device sections) & tell the second device that there is NO monitor attached (man radeon for info HowTo)

Question--do you have more than one AGP slot?--if so, is this card in a different slot than before?

---

### Post by m0unds on 2005-08-11
Only one AGP slot. Old card was dualhead as well, so I would assume that wouldn't change anything, as there are displays connected to both. (I don't use dualdisplay under lunix, only Windoze.) 

As far as the PCI ID, is there any way to probe the hardware for the present PCI location of a device?

---

### Post by autocrosser on 2005-08-11
Well-If your MB has only one AGP slot the PCI address should not have changed---I'm not sure why Xorg is asking for a non-existant slot---look at the man and I guess I'd define a second device section with the No monitor attached option--keep a rescue disc close & reboot--if it blows up, reboot with the rescue disc & re-set your old xorg.conf--

I don't have a idea why it would assign a second PCI within one card/AGP slot--maybe the ATI drivers are not compatable with the card--You said the "old"? card is a 9800 Pro?  or is this the card you are trying to enable? I run a 9600 Pro & it was a $#@## to get running with dual monitors--anyway, tread lightly with the xorg mod & post back the results---

---

### Post by m0unds on 2005-08-15
ok, well, i tried installing the new ATI driver off the ATI website, and it still has the same problem. I reverted the PCI location for the AGP slot to where it stated it was during a working config (with the 9800 pro) 


still isn't working correctly. 

i think there might just not be support for this particular card as of yet-- the chipset is recognized and is enumerated by ubuntu, but i don't think it knows what to do with the card, since it's a different chipset than is supported.

blah.

edit: from the ATI site:
New ATI Hardware Product Support

This release of the ATI Proprietary Linux driver introduces support for the following ATI Products:

    * Radeon® X800 XL
    * Radeon® X850 PRO
    * Radeon® X850 XT
    * Radeon® X850 XT Platinum Edition 


DOH. it's installed but doesn't work..and the hardware is supported. kuh-rap.

---

### Post by autocrosser on 2005-08-16
Well-I guess it's wait til the next version of Xorg & hope---

---

### Post by m0unds on 2005-08-16
yea. i think it's definitely a card support issue. I got a new hard disk and reinstalled hoary on it-- when i tried to initialize the display with fglrx, it got the same error with a clean install. 

i can't get the ATI packaged FGLRX driver to install at all, it warns about GLIBC incompatibility, which is irritating, because I can't find any way to update GLIBC (i think the ATI tool is misreading the version number of glibc..it says it's 2.1..) 

but it says "FAILED TO INSTALL FGLRX DRIVER" every time without fail. 


not sure what to do. blah.

---

