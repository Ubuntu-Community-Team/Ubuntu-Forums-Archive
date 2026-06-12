---
title: "Screen resolution"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Dustin Wyatt on 2005-04-22
Ok, I followed the instructions found [here](http://ubuntuforums.org/showthread.php?t=21984) to customize resolutions for my new monitor.  

Two problems:

1.)  X won't default to 1280x1024.  Everytime I boot up, X is at 1024x768.

2.)  When I System>Preferences>Screen Resolution and change to 1280x1024 my mouse pointer is still constrained to only 1024x768 pixels....which is not good.

My xorg.conf:

```
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
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
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"RenderAccel"		"true"
	Option		"NvAGP"			"1"
EndSection

Section "Monitor"
	Identifier	"DELL P1110"
	HorizSync	30-121
	VertRefresh	48-160
	Option		"DPMS"
	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"DELL P1110"
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

```


Help?

---

### Post by diebels on 2005-04-22
What if you use the name of your custom modline "1280x1024_85.00" in the Screen-Display section?

---

### Post by Dustin Wyatt on 2005-05-03
Hmm, no luck.

```

Section "Device"
	Identifier	"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:5:0"
	Option		"RenderAccel"		"true"
	Option		"NvAGP"			"1"
EndSection

Section "Monitor"
	Identifier	"DELL P1110"
	HorizSync	30-121
	VertRefresh	48-160
	Option		"DPMS"
	# 1280x1024 @ 85.00 Hz (GTF) hsync: 91.38 kHz; pclk: 159.36 MHz
	Modeline "1280x1024_85.00"  159.36  1280 1376 1512 1744  1024 1025 1028 1075 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
	Monitor		"DELL P1110"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_85.00"
	EndSubSection
EndSection

```

I changed my Screen section to only have 1280x1024.  I also tried it with "1280x1024_85.00" and just plain "1280x1024".  It still only boots to 1024x768 which I don't understand.  It seems like the only thing it should be able to boot to is 1280x1024 since that's the ONLY resolution in my xorg.conf.

On another note, when I go to System>Preferences>Screen Resolution and change my resolution I can now use my mouse correctly.  The problem stemmed from my use of Synergy.  I just restarted the Synergy client and all was well.

---

### Post by momo66 on 2005-05-03
What kind of video card do you have.  You might need to upgrade the drivers.

---

### Post by davegod75 on 2005-05-03
ubuntu really needs to make this easier.

why can't it be as easy as windows?

so many people with problem

---

### Post by Dustin Wyatt on 2005-05-31
[QUOTE=momo66]What kind of video card do you have.  You might need to upgrade the drivers.[/QUOTE]
 I have an Nvidia Geforce 2 GTS with the drivers installed as per [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

[quote="davego75"]ubuntu really needs to make this easier.

why can't it be as easy as windows?

so many people with problem[/quote]

I agree that this seems to be one of the bigger problems with ubuntu and linux desktop environments in general.

---

### Post by leo.nava on 2005-05-31
[http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto](http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto)

this helped me, i had the same problem as you..and now i have my excellently working
1280x1024 :)

---

