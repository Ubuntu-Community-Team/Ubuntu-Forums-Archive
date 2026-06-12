---
title: "xinerama with radeon driver &amp; ati 9550"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by lmh on 2005-06-21
Hi all,

I have a problem getting xinerama working with my Radeon 9550-Card (HIS-Card with Radeon 9550 chipset.)
I have two identical HP 2035 - LCDs and try to use the radeon-driver.
The same setup worked once, but I lost the xorg.conf - File during reinstallation of my system.

The problem:
I tried around for hours with the xorg.conf - File and lots of manuals. To me everything in the conf-file seems quite logical, but the second screen displays only a copy of the first screen, whatever I try.

My xorg.conf:

```
Section "ServerFlags"
	Option 		"Xinerama" "true"
EndSection


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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
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
	Identifier	"radeon 1"
#	Driver		"ati"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
#	Screen		1
EndSection

Section "Device"
	Identifier	"radeon 2"
#	Driver		"ati"
	Driver		"radeon"
	BusID		"PCI:1:0:1"
#	Option		"MergedFB"		"false"
EndSection

Section "Monitor"
	Identifier	"hp L2035 1"
	HorizSync   	30-92
	VertRefresh 	30-92
	Option		"DPMS"
EndSection

Section "Monitor"
    	Identifier  	"hp L2035 2"
    	HorizSync   	30-94
    	VertRefresh 	48-85
    	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen 1"
	Device		"radeon 1"
	Monitor		"hp L2035 1"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen 2"
	Device		"radeon 2"
	Monitor		"hp L2035 2"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#	Screen		0 "Screen 1" 0 0
#	Screen		1 "Screen 2" RightOf "Screen1"
	Screen		0 "Screen 1"
	Screen		1 "Screen 2" RightOf "Screen1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	Option		"Xinerama" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

``` 


$ lspci gives me following:
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4153
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4173

```


I would really apreciate a hint on what I do wrong or even a kick into the right direction.

Thanks a lot!

LMH

**LOGFILE:**
Ps.: I wanted to upload / include the log - File, but it is too big.
So here is the link:
[http://www.koeln.it/xorg-log.txt](http://www.koeln.it/xorg-log.txt)

---

### Post by lmh on 2005-06-22
nobody that has an idea or who could send me a working conf-file?

---

### Post by lmh on 2005-06-22
OK PEOPLE, I GOT IT WORKING   \\:D/ 

here my config-file for interested others:
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
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
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
	Identifier	"radeon 1"
	Driver		"radeon"
#	BusID		"PCI:1:0:0"
	Option "MergedFB" "True"
	Option "CRT2HSync" "30-92"
	Option "CRT2VRefresh" "30-92"
	Option "MonitorLayout" "LCD,LCD" #use LCD,CRT even if you have 2 CRTs
	Option "OverlayOnCRTC2" "true"
	Option "MetaModes" "1600x1200-1600x1200"
	Option "CRT2Position" "RightOf"
EndSection


Section "Monitor"
	Identifier	"hp L2035 1"
	HorizSync   	30-92
	VertRefresh 	30-92
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier "MergedFB Screen"
	Device "radeon 1"
	Monitor "hp L2035 1"
	DefaultDepth 24
	SubSection "Display"
	Depth 24
	Modes "1600x1200"
	Virtual 3200 1200
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"MergedFB Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

---

