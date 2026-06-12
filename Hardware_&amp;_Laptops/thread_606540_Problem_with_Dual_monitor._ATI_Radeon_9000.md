---
title: "Problem with Dual monitor. ATI Radeon 9000"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by eyeblack on 2007-11-08
Hello,
I recently installed Kubuntu Gutsy 7.10 on a Dell Latitude D600 w ATI Radeon Mobility 9000.
The laptop monitor is capable of resolutions up to 1400x1050 and I have an external monitor (DELL 2407WFP-HC) which is capable of resolutions up to 1920x1200.
I use the open source 'ati' or 'radeon' driver.
The problem is that I cannot set the external monitor to work at the max resolution.
The best resolution I can get is 1280x1024@75Hz.
Xrandr recognizes the resolutions of the external monitor without (obvious) problem.


> VGA-0 disconnected (normal left inverted right)
DVI-0 connected (normal left inverted right)
   1920x1200      60.0 +
   1600x1200      59.9
   1680x1050      60.0
   1280x1024      75.0     59.9
   1152x864       74.8
   1024x768       75.1     60.0
   800x600        75.0     60.3
   640x480        75.0     60.0
   720x400        70.1
LVDS connected 1400x1050+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050      60.0*+
   1280x800       60.0
   1280x768       60.0
   1024x768       60.0
   800x600        60.3
   640x480        59.9
S-video disconnected (normal left inverted right)


When I try to use resolutions larger than 1280x1024 I get a black screen. The monitor LED is on, which means that it receives signal from the laptop but remains black. The monitor does not show any "out of range" error message.

I have tried to play with Xinerama, MergeFB without success, 

Here is the relevant part of  my xorg.conf file

> #########################################
Section "Device"
	Identifier	"ATI Radeon"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Vendorname	"ATI"
EndSection

Section "Monitor" 
	Identifier	"Laptop"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"External"
	Vendorname	"Dell"
	Modelname	"LCD 1920x1200"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon"
	Defaultdepth	24
	Monitor		"Laptop"
	SubSection "Display"
		Depth	24
		Viewport	1920 0
		Virtual		3320 1200
		Modes		"1920x1200" "1400x1050"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"AIGLX"		"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"		"Enable"
EndSection

 

I have spent the last five evenings-nights-early mornings trying to find a solution so any help is more than welcome.

Thanks for your time.

---

### Post by swatson on 2007-11-15
I'm also having this problem.

Strange thing is, the background is stretched across the whole resolution, but the gnome bars both stop as if the monitor wasn't widescreen!

Any tips?

---

### Post by Scothiam on 2007-11-18
Hi everyone,
Are you guys trying to use your exteranl monitor as your primary desktop, or as a second display (big desktop).
I've had a similar experience with my Dell 600m radeon mobility 9000 64mb, although to clarify, my external display only mirrors the primary (with the menu bar anomally already mentioned).
The only luck I've had in getting dual display working was to install 6.06 and edit the xorg.conf file extensively...
Would love to have it working with the current desktop Os however...
here is my working xorg.conf file in Ubuntu 6.06, trying to update/modify for 7 or 7.10...

the only main differance I can tell imediatly is that the previous xorg.conf file posted has only one ATI "device" (each "screen" needs to be linked to it's own ATI "device"), not sure if that matters in ubuntu 7+

> 
Section "ServerLayout"	
	Identifier 	"Dualhead Layout"
	Screen 0 	"Laptop Screen" 0 0
	Screen 1 	"LG Screen" RightOf "Laptop Screen"
	InputDevice 	"Generic Keyboard"
	InputDevice 	"Configured Mouse"
	InputDevice 	"Synaptics Touchpad"
	Option 		"AIGLX" "true"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/X11/fonts/CID" #added
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID" #added
EndSection

Section "Module"
	Load  "GLcore" #added
	Load  "i2c" #added	
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
	#...blah blah blah, I've cut this out for this forum
EndSection

Section "Monitor"
	Identifier   "Laptop Monitor"
	#HorizSync    28.0 - 49.0
	#VertRefresh  43.0 - 72.0
	Option	     "DPMS
EndSection

Section "Monitor"
	Identifier   "LG Monitor"
	VendorName   "LG"
	#ModelName   "SyncMaster 900NF"
	#HorizSync   30-86
	#VertRefresh 50-160
	Option	     "ModelName" "Generic Autodetecting Monitor"
	Option       "DPMS" "true"
EndSection

Section "Device" # Device 1 for primary laptop display
	Identifier   "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver       "radeon" #changed from "ati"  CHANGED 4 3d
	BusID 	     "PCI:1:0:0"
	Screen 0
#Optimized values (changed from driver default?)
	Option       "DRI" "true"
	Option       "ColorTilling" "on"
	Option       "EnablePageFlip" "on" #changed from "true"  CHANGED 4 3d
	Option       "AccelMethode" "EXA"
	Option       "XAANoOffscreenPixmaps" "true"
	Option       "RenderAccel" "true"
	Option       "AGPMode" "4" #changed from 8  CHANGED 4 3d
	Option       "AGPFastWrite" "on"
	Option	     "SWcursor" "off" #Faster than default (on) ADDED 4 3d
	Option	     "DynamicClocks" "on" #ADDED 4 3d
	Option	     "BIOSHotkeys"   "on" #ADDED 4 3d
#These are not mentioned in man page for driver
	Option		"AGPSize" "32" # default: 8 #ADDED 4 3d
	Option		"EnableDepthMoves" "true" #ADDED 4 3d
EndSection

Section "Device" # Device 2 for external display
	Identifier   "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf) 2"
	Driver       "radeon" #changed from "ati"  CHANGED 4 3d
	BusID        "PCI:1:0:0"
	Screen 1
EndSection

Section "Screen"
	Identifier   "Laptop Screen"
	Device       "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Monitor      "Laptop Monitor"
	DefaultDepth     24
	#...I've only shown my desired res for this post
	SubSection "Display"
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier "LG Screen"
	Device "ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf) 2"
	Monitor "LG Monitor"
	DefaultDepth 24
	#...I've only shown my desired res for this post
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection

Section "ServerFlags"
	Option "Xinerama" "ON"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option 	"Composite" "false"
EndSection


---

### Post by eyeblack on 2007-12-02
Update:
After several days of trial and error I have found the following.
a. I was not able to get the resolution I want using mergedFB or Xinerama,
b. xrandr seems to be the only method to get dual monitor support however I cannot get a resolution of 1400x1050 on laptop monitor and 1900x1200 on the external monitor at the same time.
c. I can get the dual monitor when I use 1400x1050 on the laptop monitor and up to 1280x1024 on the external monitor. Any resolution above that results to a black external screen.
The commands I use are:
$ xrandr --output LVDS --mode 1400x1050
$ xrandr --output DVI-0 --left-of LVDS --mode 1280x1024
and in the xorg.conf I have set a virtual desktop of 
3320x1200

d. Using xrandr and single monitor output I am able to get the 1400x1050 on the laptop monitor and up to 1680x1050 on the external monitor.
The commands I use are:
$ xrandr --LVDS --off
$ xrandr --DVI-0 --mode 1680x1050 --rate 60.0

It seems that any resolution with vertical resolution >1050 does not work. I do not know if this is a limitation of the radeon driver or a limitation imposed by the maximum vertical resolution of the laptop.

Any ideas welcome.

---

### Post by reiny on 2008-01-18
Hi eyeblack,

there really seems to be no way to scale up the resolution,
I have also tried out a lot of things and ripped out a bunch of my hair as well... :)

I am also working with a D600 Notebook at the native resolution of 1400*1050 and attached the same monitor as you.

At least I would like to make use of the 1680x1050 widescreen resolution instead of stretched 1280x1024. Single monitor support would be sufficient.

Could you post again your configuration for that single screen mode?When I run xrandr the widescreen resolutions are not listed :(

Do you also know a way how to automatically switch to the external screen at startup automatically.

I am sorry that I could not provide further hints on your problem - except that I also read a lot of posts without result.

I would really appreciate to receive an answer from your side.

Thanks a lot in advance.
 ! :)

---

### Post by Yellow Pasque on 2008-01-18
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

---

