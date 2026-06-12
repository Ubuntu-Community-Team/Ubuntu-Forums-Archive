---
title: "Toshiba R100 VGA output"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by mmrr on 2007-04-09
Hello Ubuntu Users!


Does anyone have any experience with a Toshiba R100 external VGA output? The notebook uses the Trident Cyberblade XP graphic chip. 

I'm trying to use the external output with a resolution of 1600x1200, which I'm not sure whether it is supportet by the trident driver or not. 

It works fine with the native lcd resolution of 1200x768 but not with the higher resolution.

Maybe someone can help...

Thanks. 
Matthias


PS: my xorg.conf file:


```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "GLcore"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
	Load  "type1"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	#DisplaySize	  410   310	# mm
	Identifier   "Monitor0"
	VendorName   "ENC"
	ModelName    "S2000"
 ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    24.0 - 94.0
	VertRefresh  49.0 - 86.0
	Option	    "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "PciRetry"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SetMClk"            	# <freq>
        #Option     "MUXThreshold"       	# <i>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "NoMMIO"             	# [<bool>]
        #Option     "NoPciBurst"         	# [<bool>]
        #Option     "MMIOonly"           	# [<bool>]
        #Option     "CyberShadow"        	# [<bool>]
        #Option     "CyberStretch"       	# [<bool>]
        #Option     "XvHsync"            	# <i>
        #Option     "XvVsync"            	# <i>
        #Option     "XvBskew"            	# <i>
        #Option     "XvRskew"            	# <i>
        #Option     "FpDelay"            	# <i>
        #Option     "Display1400"        	# [<bool>]
        Option     "Display"            	"crt" 
        #Option     "GammaBrightness"    	# [<str>]
        #Option     "TVChipset"          	# [<str>]
        #Option     "TVSignal"           	# <i>
	Identifier  "Card0"
	Driver      "trident"
	VendorName  "Trident Microsystems"
	BoardName   "CyberBlade XP4m32"
	BusID       "PCI:1:0:0"
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
		Modes	"1600x1200" "1024x768"
	EndSubSection
EndSection

```

---

### Post by egfrith on 2007-04-18
Hello there,

I'm afraid I can't help but I'm quite impressed that you can get any decent output at all. I've not tried myself with a data projector with that driver under Ubuntu, but  a colleague with the same laptop (but running Fedora) has not had any joy. 

The way to get VGA output used to be to use the vesa driver, but this seems to be broken in Edgy:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/68814](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-vesa/+bug/68814)
[http://ubuntuforums.org/showthread.php?t=301082](http://ubuntuforums.org/showthread.php?t=301082)

---

### Post by mmrr on 2007-04-19
I solved the problem using the fbdev driver and the vesafb-tng framebuffer. With this settings i can get a resolution of 1600x1200 for the vga output. But is not accelerated. 

Now I'm  working on the acceleration. I'm trying to use the tridentfb framebuffer, which is supposed to have acceleration. But until now with no success. 

Any suggestion or experience with the tridentfb framebuffer? Settings for the kernel configuration?

Thank you.
matthias

---

