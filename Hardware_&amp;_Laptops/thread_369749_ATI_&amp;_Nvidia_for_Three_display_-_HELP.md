---
title: "ATI &amp; Nvidia for Three display - HELP?"
date: 2007-02-24
forum: Hardware &amp; Laptops
---

### Post by deathshadow on 2007-02-24
I'm biting the bullet and actually trying to see if I can configure my primary workstation to use Edgy for a week... 3d design (3ds Max/Blender), Web Design (So I'll be running IE6 & 7 via Wine), programming (blessed be the gedit!) So far, it's been going fairly smooth. I know enough linux to handle most configs since all my servers run either Ubuntu or Sarge and I use it on one of my laptops... Yet I've avoided it on my workstation (staying with XP) because A> It's also a gaming box, and B> I've been running three displays on two different video cards:

Ge7600GT - IBM 21" CRT Center
Radeon 9250 - Eizo 21" CRT Left, Samtron 17" CRT Right

So far, all I can say is MAN - what a load of bull to have to wade through for basic functionality I had in Windows 3.1 with third party drivers and was built into MacOs System 6 and Win98. I know most everything in the 'Linux Desktop' lags a decade behind 'Rest of World' thanks to the royal pain in the *** it is to configure X11, but SHEESH. Of course, my own damned fault - I can get two monitors working just fine, I just REALLY got used to using three...

Anyhow, here's what I tried... *(I made some 'corrections' to my xorg.conf - MAN, what's with the default file calling all those directories and devices that don't exist, or the /TrueType directory not even having a fonts.dir file setup?)* 

First, I just figured I'd set it up as three separate displays then tie them together with Xinerama:

```

Section "Files"
	# path to defoma fonts
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	 "Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc101"
	Option		"XkbLayout" "us"
	Option		"XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "false"
EndSection

Section "Monitor"
	Identifier	"IBM 6652 P27"
	VendorName	"IBM"
	ModelName	"IBM 6652 P275"
	DisplaySize	400 300
	HorizSync	30-130
	VertRefresh	48-170
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Eizo FlexScan 930F"
	VendorName	"Eizo"
	ModelName	"Eizo FlexScan 930F"
	DisplaySize	400 300
	HorizSync	30-92
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Samtron 76DF"
	DisplaySize	320 240
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Ge7600GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Option		"NoLogo" "on"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9250 5960"
	Driver		"ati"
	BusID		"PCI:01:06:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"ATI Radeon 9250 5960 Secondary"
	Driver		"ati"
	BusID		"PCI:01:06:1"
	Screen		1
EndSection

Section "Screen"
	Identifier	"Center"
	Device		"nVidia Ge7600GT"
	Monitor		"IBM 6652 P27"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1920x1440" "1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
	Option		"RenderAccel" "true"
	Option		"CoolBits" "on"
	Option		"NoLogo" "on"
EndSection

Section "Screen"
	Identifier	"Right"
	Device		"ATI Radeon 9250 5960"
	Monitor		"Samtron 76DF"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Left"
	Device		"ATI Radeon 9250 5960"
	Monitor		"Eizo FlexScan 930F"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1920x1440" "1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Center" 0 0
	Screen		"Right" RightOf "Center"
	Screen		"Left" LeftOf "Center"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "true"
EndSection

```

But apparantly the ATI driver refuses to not put BOTH outputs of the same card side by side - which is REALLY stupid IMHO... If you put the 'right rightof center' first, BOTH end up on the right, if you put the 'left' first, they BOTH end up on the left... either way, the Eizo refuses to run anything other than 800x600 on that ATI card.

No big deal I figure, Windows is easy enough to change the ports so I'll just plug the Eizo into the Ge7600GT

```

Section "Files"
	# path to defoma fonts
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	 "Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc101"
	Option		"XkbLayout" "us"
	Option		"XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "false"
EndSection

Section "Monitor"
	Identifier	"IBM 6652 P27"
	VendorName	"IBM"
	ModelName	"IBM 6652 P275"
	DisplaySize	400 300
	HorizSync	30-130
	VertRefresh	48-170
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Eizo FlexScan 930F"
	VendorName	"Eizo"
	ModelName	"Eizo FlexScan 930F"
	DisplaySize	400 300
	HorizSync	30-92
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Samtron 76DF"
	DisplaySize	320 240
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Ge7600GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Screen		0
	Option		"NoLogo" "on"
	Option		"UseEDIDFreqs" "FALSE" # let Eizo run at >800x600
EndSection

Section "Device"
	Identifier	"nVidia Ge7600GT Secondary"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
	Screen		1
EndSection

Section "Device"
	Identifier	"ATI Radeon 9250 5960"
	Driver		"ati"
	BusID		"PCI:01:06:0"
EndSection

Section "Screen"
	Identifier	"Center"
	Device		"nVidia Ge7600GT"
	Monitor		"IBM 6652 P27"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1920x1440" "1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
	Option		"RenderAccel" "true"
	Option		"CoolBits" "on"
	Option		"NoLogo" "on"
EndSection

Section "Screen"
	Identifier	"Right"
	Device		"ATI Radeon 9250 5960"
	Monitor		"Samtron 76DF"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Left"
	Device		"nVidia Ge7600GT Secondary"
	Monitor		"Eizo FlexScan 930F"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1920x1440" "1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Center" 0 0
	Screen		"Left" LeftOf "Center"
	Screen		"Right" RightOf "Center"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "true"
EndSection

```

That nice little "UseEDIDFreqs" line lets the Eizo run at my desired 1920x1440 (WHOO! Is there a ATI equivalent to that?) BUT that bombs with a wonderful:

```

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/bin/X11/X(main+0x475) [0x806e705]
3: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d858cc]
4: /usr/bin/X11/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

```

Disabling Xinerama so they are all independant desktops makes it run just fine... But that's NOT what I want/need.

So... I try something REALLY out there... What if I run the two nV outputs as twinview, then xinerama the 9250 to the left?

```
Section "Files"
	# path to defoma fonts
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	 "Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc101"
	Option		"XkbLayout" "us"
	Option		"XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device" "/dev/input/mice"
	Option		"Protocol" "ExplorerPS/2"
	Option		"ZAxisMapping" "4 5"
	Option		"Emulate3Buttons" "false"
EndSection

Section "Monitor"
	Identifier	"IBM 6652 P27"
	VendorName	"IBM"
	ModelName	"IBM 6652 P275"
	DisplaySize	400 300
	HorizSync	30-130
	VertRefresh	48-170
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Samtron 76DF"
	DisplaySize	320 240
	HorizSync	30-70
	VertRefresh	50-160
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Ge7600GT"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9250 5960"
	Driver		"ati"
	BusID		"PCI:01:06:0"
EndSection

Section "Screen"
	Identifier	"TwinView Screens"
	Device		"nVidia Ge7600GT"
	Monitor		"IBM 6652 P27"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1920x1440" "1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
	Option		"TwinView" "on"
	Option		"MetaModes" "CRT-0:1920x1440, CRT-1:1920x1440"
	Option		"RenderAccel" "true"
	Option		"HorizSync" "CRT-0:30-130; CRT-1:30-92"
	Option		"VertRefresh" "CRT-0:48-170; CRT-1:50-160"
	Option		"CoolBits" "on"
	Option		"NoLogo" "on"
	Option		"TwinViewOrientation" "CRT-1 LeftOf CRT-0"
	Option		"Xinerama" "on"
	Option		"ConnectedMonitor" "CRT,CRT"
	Option		"UseEDIDFreqs" "FALSE" # let Eizo run at >800x600
	Option		"TwinViewXineramaInfoOrder" "CRT-0,CRT-1"
EndSection

Section "Screen"
	Identifier	"Right"
	Device		"ATI Radeon 9250 5960"
	Monitor		"Samtron 76DF"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"1600x1200" "1280x960" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"TwinView Screens" 0 0
	Screen		"Right" 3840 480 # push it down while here
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"Xinerama" "true"
	Option		"Clone" "On"	
EndSection

```

Which appears to work at first, and is the closest of all of them, but has 'problems'... as presented above Terminal won't start... no errors, little 'wait' ball sits and spins then the cursor returns to normal as if you never clicked on it... The second problem is that for some reason, twinview no longer reports Xinerama data, so maximizing a program spans BOTH left displays.

It APPEARS the problem with apps (like terminal) starting can be alleviated by commenting out the right display - If I disable that, terminal starts just fine... The other problem with twinview seems to be the 'Option "Xinerama"' line. If you turn Xinerama on, it appears to override Twinview's 'faking' Xinerama data treating the whole thing as one big screen.

SO... my question is: Does anybody know how I can get all three displays working as a single Xinerama desktop on my existing hardware - I feel like any one of these is SO close...

Oh, and is there any way to CONSISTANTLY make OpenGL apps running fullscreen ONLY open up on my CENTER display while having a wide desktop? MacOS or Win I just set it as 'display 1' - I take it the X11 world **STILL** has no equivalent? *(I LOVE how some apps in 'fullscreen' don't change the video mode and run half and half on each display - NOT)*

Really sad part is, I think from this whole thing I've learned to make dual head work fine in my sleep... yet going to three eludes me - unless of course I can live with my left display as my primary (NOT). For now I'm mapping the Left display as being between my center and right, twinview, no xinerama - it's confusing, but at least all the screens work.

---

