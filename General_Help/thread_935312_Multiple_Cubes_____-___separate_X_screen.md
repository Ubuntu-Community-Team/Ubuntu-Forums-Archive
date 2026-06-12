---
title: "Multiple Cubes  ???   -   separate X screen"
date: 2008-10-01
forum: General Help
---

### Post by eotakos on 2008-10-01
hello everyone!

i've two monitors connected to my nvidia card, and i've enabled the separate x-screen option, which means that my OS is supposed to see that i have two output devices (according to everything i've read of-course). 

Now, in the compiz settings manager, there is an option for the cube thing which controls what happens when there are multiple output devices. You can either have one big cube, or you can have multiple cubes. If I change this option nothing happens - the current situation is that i have two cubes, one in the primary monitor with the settings i had before - and i control through the compiz manager, and another in the secondary monitor which has only two desktops - this i can't change. Everything i do applies to the primary monitor & cube

any ideas?


thanks in advance

---

### Post by eotakos on 2008-10-01
actually the thing is that i can't change the number of workspaces

---

### Post by chingchong on 2008-11-02
OK I'm having the same problem, I am definitely not a noob to linux. 
I have this feature working fine in Fedora 9, decided to try Ubuntu agian when 8.1 came out. Generally enjoying 8.10 but the little things like this frustrate me with the inconsistencies of linux distros.   
Tried all suggested remedies, no result.
YES I changed # of workspaces to 4 from 2 :D

I have a NVidia 8800GTX, which is working but, the nvidia-settings will not save to XORG file. I've tried gksudo and sudo nvidia-settings, and ran nvidia-xconfig as described in this thread [SOLVED nvidia-settings do not save to X Config File]("http://ubuntuforums.org/showthread.php?t=961348"). I'm also running Twin View thought about separate X, but since nvidia-settings won't save, not really an option. Anyway I'll continue looking for a solution, but this could be related to video card issues instead of compiz settings. If anyone has any input please help, otherwise I'm going back to Fedora for now. FYI I know how to manually change xorg file but I don't consider that an acceptable solution, I think there are too many Linux distros that have matured beyond that to settle for anything less. Please Advise.

---

### Post by loomsen on 2008-11-02
None of the above.

It's just, X doesn't really like to be configured while running... 
It would be like changing a cars tire while driving 200.

So, what you can do, if you really want to use nvidia-settings to configure it for you... Run it as normal user, no need for sudo messing around, configure it, hit save to x configuration file, and chose some other path you have write permissions on, for instance lets say
~/x-conf/xorg.conf. 
If you're promted that no xorg.conf has been found to merge it with, you probably didn't uncheck that option :) Anyway, you may ignore that hint.

Oh, what you should be aware of tho, nvidia settings will have your keyboard configured with QWERTY layout, so, if you're from anywhere else in the world add your desired layout prior to saving. Just klick preview and edit it, I add these options for instance:
```

	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"

```

Then drop yourself into a terminal with Alt+Ctl+F2 for example, and login.

Get root with

```
sudo -i
```
and run this to stop gnome

```
/etc/init.d/gdm stop
```

Now, backup your xorg.conf and copy the file you generated through nvidia-settings. You will have to remove your xorg.conf before you can create another one, so sth like this should be what you want:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak && rm /etc/X11/xorg.conf
cp /home/$USER/x-conf/xorg.conf /etc/X11/xorg.conf
exit
startx

```

NOTE: You will have to replace $USER with your actual username, cause you should be root when running this cmd, so it would mislead to /home/root/... if you don't replace it.

Enjoy, here's my xorg with separate X-Screen setup, I've got my LCD TV attached to my Laptop.


IT IS VERY LIKELY THAT YOU'LL HAVE TO CHANGE SOME THINGS TO YOUR NEEDS HERE N THERE. Like Monitor resolution, I hope you are aware of that.
But you've got something working to start from, have fun...

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice	   "Synaptics Touchpad"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
    Load           "dbe"
    Load		"record"
    Load		"dri"
EndSection

Section "ServerFlags"
    Option		"Xinerama"	"0"
EndSection

Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"			"auto"
	Option		"Device"				"/dev/psaux"
	Option		"Emulate3Buttons"		"no"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"		"True"
	Option		"Device"				"/dev/psaux"
	Option		"Protocol"			"auto-dev"
	Option		"HorizTwoFigerScroll"	"True"
	Option		"VertTwoFingerScroll"	"True"
EndSection

Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
	Identifier	"Monitor0"
	VendorName	"Unknown"
	ModelName	"CPT"
	HorizSync	30.0 - 75.0
	VertRefresh	60.0
	Option		"DPMS"
EndSection

Section "Monitor"
    # HorizSync source: builtin, VertRefresh source: builtin
	Identifier	"Monitor1"
	VendorName	"Unknown"
	ModelName	"CRT-0"
	HorizSync	28.0 - 55.0
	VertRefresh	43.0 - 72.0
	Option		"DPMS"
EndSection

Section "Device"
    Identifier		"Videocard0"
    Driver			"nvidia"
    VendorName		"NVIDIA Corporation"
    BoardName		"GeForce 8600M GT"
    BusID          	"PCI:1:0:0"
    Option			"AllowIndirectPixmaps"		"true"
    Option			"Coolbits"	"1"
    Option 	   		"AllowGLXWithComposite"	"true"
#    Option	   		"XAANoOffscreenPixmaps"
	Option		"NoLogo"	"true"
    Screen       		0
EndSection

Section "Device"
    Identifier		"Videocard1"
    Driver			"nvidia"
    VendorName		"NVIDIA Corporation"
    BoardName		"GeForce 8600M GT"
    BusID			"PCI:1:0:0"
    Option			"AllowIndirectPixmaps"		"true"
    Option			"Coolbits"	"1"
    Option			"AllowGLXWithComposite"	"true"
#    Option			"XAANoOffscreenPixmaps"
	Option		"NoLogo"	"true"
    Screen			1
EndSection

Section "Screen"
# Laptop
    Identifier		"Screen0"
    Device			"Videocard0"
    Monitor		"Monitor0"
    	DefaultDepth    	24
    Option			"TwinView" "0"
    Option			"AllowGLXWithComposite"	"true"
#   Option 			"PixmapCacheSize" "2000000"
#	Option 			"AllowSHMPixmaps" "0"
    Option			"AddARGBGLXVisuals"		"true"
    Option			"TwinViewXineramaInfoOrder" "DFP-0"
#    Option			"metamodes" "DFP: 1440x900 +0+0"
#    Option			"DPI"		"110 x 108"
    SubSection		"Display"
        Depth			24
        Modes		"1440x900"
    EndSubSection
EndSection

Section "Screen"
# Fernseher
    Identifier		"Screen1"
    Device			"Videocard1"
    Monitor		"Monitor1"
    	DefaultDepth		24
    Option			"TwinView"	"0"
    Option			"TVStandard"	"PAL-B"
#	Option 			"PixmapCacheSize" "2500000"
#	Option 			"AllowSHMPixmaps" "0"
    Option			"AllowGLXWithComposite"	"true"
    Option			"AddARGBGLXVisuals"		"true"
#    Option			"metamodes" "CRT: 1360x768 +0+0,1024x768 +0+0"
#    Option			"DPI"		"100 x 75"
    SubSection		"Display"
	Depth			24
#	Modes		"nvidia-autoselect"
	Modes		"1024x768"
    EndSubSection
EndSection

Section "Extensions"
	Option 	"Composite"	"Enable"
	Option 	"RENDER"	"true"
	Option 	"DAMAGE"	"true"
EndSection

```

[color=red]So read this file to the very end of it and comment everything you're not quite sure about out with prepending a # to the respective line
[/color]

---

