---
title: "NVIDIA vs NV"
date: 2005-11-23
forum: General Help
---

### Post by art2003 on 2005-11-23
when I have "nv" on xorg.conf
"everything works except glxgears where I get an error:
Xlib: extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual

and naturally GLX games don't work


when I have "nvidia" on xorg.conf
Then glxgears works, Quake 3 works but applications which expect Xv don't work (such as VDR)
with "nvidia" xvinfo says there are no Xv extensions.

My /etc/modules :```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
dvb_ttpci
nvidia
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
amd74xx
ide-cd
ide-disk
ide-generic

My /etc/X11/xorg.conf

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load    "GLcore"
        Load	"bitmap"
	Load	"dbe"
	Load	"ddc"

        #Load    "dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option  "NoLogo"
EndSection

Section "Monitor"
	Identifier	"Acer AL1912"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440]"
	Monitor		"Acer AL1912"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

Any help greatly appreciated.

---

### Post by metoo on 2005-11-24
Are you using the nvidia stuff from linux-modules-restricted-2.6...your-kernel?
(Hm, MX440, not sure, if you need the legacy driver instead...??, but if the 3D stuff works, you should be OK)

While not using xv much, here a 6800gt agp lists lots of settings on xvinfo.
However, I've comment out 'GLcore' .
I think this should be with the nvidia kernel driver.

Maybe this helps.

My section module:
Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
#	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

And UT2k4 is running strong ! :-)

---

### Post by art2003 on 2005-11-24
Thanks Metoo for your help, I have implemented your proposed changes and now xvinfo and glxgears work, Quake2 works perfectly, quake3 works but no sound. Heroes3 also works but no sound. It seems that sound in linux is a bit chancy at best?
In multimedia settings I have all ESD, alsa and oss working

 xawtv uses to work by default but now works only if I launch it as
xawtv -device /dev/video0

---

