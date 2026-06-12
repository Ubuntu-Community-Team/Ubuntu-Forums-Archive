---
title: "DisplayLink WS Tech USB-DVI Ubuntu 11.04 x86_64"
date: 2011-05-15
forum: Hardware
---

### Post by oceallaighm on 2011-05-15
Ubuntu 11.04 x86_64, kernel 2.6.38-9 generic.
DisplayLink WS Tech USB-DVI

dmesg: extract
DisplayLink USB device /dev/fb0 attached. 1280x768 resolution. Using 3840K framebuffer memory
usbcore: registered new interface driver udlfb

Xorg --configure detected all 3 monitors, internal laptop, DisplayLink and external vga in that order and created an xorg.conf.new file which I copied to /etc/X11/xorg.conf. The is using the open source driver radeon for the laptop monitor, fbdev for the DisplayLink monitor and vesa for the external vga monitor.

Added:
Option         "Xinerama" "0"

ModulePath   "/usr/local/lib/xorg/modules/drivers"
ModulePath   "/usr/lib/xorg/modules"
ModulePath   "/usr/lib/xorg/modules/drivers"
ModulePath   "/usr/local/lib"

lsusb shows which I understand to be the DisplayLink device.
Bus 001 Device 003: ID 17e9:0198 Newnham Research

I get a green screen on the DisplayLink monitor but only the laptop and the eternal vga monitor work.

Note:
libusb-dev was installed from the Ubuntu repository as was xserver-xorg-video-displaylink.

/etc/gdm/Init/Default
XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
  $XRANDR -o 0
fi

libdlo
./configure && sudo make install && make check 
This works, I get the graphics output on the DisplayLink montor.
I then ran 
./configure && sudo make install && make

I reboot Ubuntu, I still only get the internal and external monitor and the DisplayLink device remains green. With the external vga monitor unplugged, I was able to get Ubuntu 10.10 in recovery mode to run a terminal and in low resolution use the DisplayLink device, it defaulted to being the primary the (only) monitor and I got no output from the laptop's internal monitor. Having the DisplayLink device for 3 years now and being able to use all three monitors in Windows 7, I would now like to do the same in Ubuntu, as this has been my default OS since Ubuntu 8.04. Any ideas?

Update:-

I copied the xorg.conf file that Xorg had generated to usr/share/X11/xorg.conf.d/10-monitor.conf. I edited the file by changing the order in the DEVICE section of the file so that displaylink was first, radeon was second and vesa third, I checked that the other sections reflected this change. I restarted Ubuntu. I made some progress in that I got three monitors, the displaylink one was purple, the other two had the Ubuntu background. The GDM logon was not available. The mouse was active on the displaylink monitor or on the other two together. I was unable to progress further and I could not get a terminal login.

---

### Post by sehson on 2011-07-14
Hello,

I am rather new to linux, but need to use it in my job so am learning fast.  Could you post more of the steps of how you got to where you did?  I too have one of these and I need more monitors for my new job.  Tech support (way too many windows open at one time.

Thank You.

---

### Post by Cammaaron on 2011-07-16
would like to see the steps too as I also have a displaylink device.

---

### Post by poppe076 on 2011-07-31
Any progress on this? I'm at just about the same point you are. I have no clue what to try next.

---

### Post by talthing on 2011-09-03
I am also having an issue with the same device.  I would think that if the device is being recognized, and the driver is being recognized, the monitor would show up under 'Monitors' utility and you would be able to adjust the resolution and position.

I have tried X -configure and then copying that to /etc/X11 as xorg.conf and then editing it to include the Displaylink section as well as editing the 'Serverlayout' section to point 'Screen2' as 'DisplayLinkScreen'

This made absolutely no difference.  It seems as though there is an additional file or configuration needed or edited or something.

Below is my information regarding the displaylink

Ubuntu 11.04 x86_64  2.6.38.11-generic
Displaylink - WS Tech USB-DVI


dmesg (exerpt):
[    4.459878] usbcore: registered new interface driver uvcvideo
[    4.459883] USB Video Class driver (v1.0.0)
[    4.598975] udlfb: DisplayLink WS Tech USB-DVI - serial #430225
[    4.598985] udlfb: vid_17e9&pid_0198&rev_0013 driver's dlfb_data struct at ffff880145646000
[    4.598990] udlfb: console enable=0
[    4.598993] udlfb: fb_defio enable=0
[    4.599168] xhci_hcd 0000:03:00.0: WARN: short transfer on control ep
[    4.599856] udlfb: vendor descriptor length:29 data:29 5f 01 0027 00 04 04 01 00 03

[    4.898024] udlfb: DisplayLink USB device /dev/fb1 attached. 1600x1200 resolution. Using 7504K framebuffer memory

libdlo-0.1.2 check:
test: release &2531160...
test: final...
test: finished.
PASS: test/test1
=============
1 test passed

/etc/X11/init.conf.d
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
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
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
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
	EndSubSection
EndSection

---

### Post by talthing on 2011-09-03
There is clearly another file that needs to be edited.

I've tried copying my xorg.conf file to /etc/X11/init.conf.d (overwriting the file). I've also tried copying it to /etc/X11 (as normally directed)

neither has made any change to the displaylink screen.  Nor has it affected gdm (that I can tell)

below is my xorg.conf file I'm referring to

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" LeftOf "Screen0"
	Screen      2  "DisplayLinkScreen" LeftOf "Screen1"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/local/lib"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri2"
	Load  "record"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "glx"
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
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"        	# [<str>]
        #Option     "DRI"                	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "Tiling"             	# [<bool>]
        #Option     "Shadow"             	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "RelaxedFencing"     	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card2"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
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
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
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
	EndSubSection
EndSection
############### DisplayLink Stuff ###############

Section "Device"
Identifier "DisplayLinkDevice"
driver "displaylink"
Option "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
Identifier "DisplayLinkScreen"
Device "DisplayLinkDevice"
Monitor "DisplayLinkMonitor"
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection
Section "Monitor"
Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
Identifier "DisplayLinkScreen"
Device "DisplayLinkDevice"
Monitor "DisplayLinkMonitor"
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by alex.perez@adalsys.com on 2011-09-12
Has anyone managed to make any progress?

---

