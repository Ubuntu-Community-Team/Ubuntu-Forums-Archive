---
title: "T60 Flickering Display"
date: 2008-05-01
forum: Hardware
---

### Post by Ohwii on 2008-05-01
Hi Guys,

finally after ubuntu recognizes my graphic-card I now have to problem that whenever I start a Video or the screen saver the video/ screen saver starts to flicker.

Does Anyone have experience with this issue?

I'll enclose the fglrxinfo and the xorg.conf 

Would be good if someone could help 

Ohwii

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

```

```


Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"XAANoOffscreenPixmaps"	"on"
	Option		"TexturedVideo"	"on"
	Option		"BackingStore"	"on"
	Option		"UseFastTLS"	"1"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Option		"AIGLX"	"on"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"RENDER"	"Enable"
	Option		"DAMAGE"	"Enable"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by MaindotC on 2008-05-01
I have a T60 with the x1300 and it works wonderfully (except I can't access my password-protected shares) so here's my xorg.conf if it would be of any help:

```


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1600x1200"
	Horizsync	31.5-74.7
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1600x1200@60"	"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by Ohwii on 2008-05-02
anybody else??

---

### Post by Kazz000 on 2008-05-02
I think that it is a problem with the ATI drivers. My x1650 Pro will flicker when playing games or during a screensaver unless I disable the desktop effects. It might not be the same for your setup though, I dont know. Some fullscreen games just dont work period for me sometimes. My monitor says no support and I have to quit or sometimes reboot. Maybe I will finally switch to nvidia now. :(

---

### Post by Ohwii on 2008-05-09
Bump! 

any thinkpad users??

---

### Post by Ohwii on 2008-05-12
and another one ??

---

### Post by Ohwii on 2008-05-12
CAN anybody help me PLEASE

---

### Post by miko777 on 2008-06-02
I had this problem, but solved it by turning up the opacity of my desktop cube to 100%.

It's now totally flicker free.

---

### Post by michealPW on 2008-06-26
Hi there, Ohwii! I originally found your post at forums.thinkpads.com, but that forum's messed up... I couldn't even contact that "Bill" guy to fix it, because the retard has all these anti-spam filters... Anyways, I found you!:)

Since I'm lazy, here the letter to Bill regarding you, I hope it helps:



Hello, Bill. My name's Micheal.

I had been browsing your forum, noticed a post made by one of your members... http://forum.thinkpads.com/viewtopic.php?t=61879

I noticed nobody had effectively helped the lady/sir; I was hoping to register and reply to the topic with some useful information, however your limitations and restrictions make that impossible. Banning all public eMail address', forcing people to reveal sensitive information about themselves and above all, outlining an "Administration Fee... $5.00" in your terms of use... Not exactly the way to drive added users to your site.

However, I like to help people so, If you could pass along this information to ohwii, in the topic I linked above, I'm certain he/she would appreciate it:

<<michealPW wrote>> Your screen is flickering because of your xorg.conf configuration file. The X.Org X Window System is the graphics subsystem of UNIX. It provides the graphical display you use, and all other UNIX programs use it to display things on your screen. Without properly configuring the X Window System, you will never get any other program to display properly (Essentially, as they use X.Org to output information to your screen...)

Normally, The X Server will probe your monitor's EDID (Extended Display Identification Data,) chip however like mine, your monitor may not have one. This means you will have to find the information yourself, and use it to setup the X Server.

First, establish the make and model of your monitor. Then using that information, search google until you've found first, your monitor's display size (The horizontal and vertical size of the VISIBLE screen, in millimeters. Second, your monitor's horizontal refresh rate in kHz
and third, the vertical refresh rate in Hz.

Once you've established this data, put it into your xorg.conf (Typically /etc/X11/xorg.conf,) under the Monitor section. It should look like this:

Section "Monitor"
  ....
  HorizSync    30-70kHz
  VertRefresh  50-160Hz
  DisplaySize  310 240
  ....
EndSection

Once that has been established, you'll be searching google for your Monitor's natural settings. (All monitors have "natural" settings, the ones that the monitor will look the best at.) Using those settings, you'll setup your xorg.conf Monitor section's modelines...

Next to impossible to wrap your head around, at least for me it was, my math skills aren't up to par... But using a tool called gtf, you can generate your modelines like this:

My monitor's natural settings are: 640x480@120Hz, 800x600@110Hz, 1024x768@85Hz and 1280x1024@66Hz.

Knowing that, I'll use gtf to setup the modelines like this:

gtf 1024 768 85

That produces the following modeline:

Modeline "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync

After you've used gtf to generate *all* your modelines (For all modes your monitor naturally supports,) you'll put them into your Monitor section as well, like so:

Section "Monitor"
 ....
 HorizSync    30-70kHz
 VertRefresh  50-160Hz
 DisplaySize  310 240
 Modeline "1024x768_85.00" 94.39 1024 1088 1200 1376 768 769 772 807 -HSync +Vsync
 ....
EndSection

Now, to provide all programs will a list of modes they can choose from, look in xorg.conf for your Screen section, inside it will be a Sub Section called "Display", where you'll list the supported modes (That you generated using gtf.

SubSection "Display"
 ...
 Viewport 0 0
 Depth 24
 Modes "1024x768_85.00" "800x600_110" "640x480_120"
 ...
EndSubSection

The first mode in the Modes list will be the default mode (Used by the Ubuntu.)

---

