---
title: "[SOLVED] More NVIDIA Compiz-Fusion Tearing"
date: 2008-12-01
forum: General Help
---

### Post by _AndY on 2008-12-01
I know it's been done to death, but I'm still experiencing heavy tearing in every movement on my screen when running Compiz. I have spent many hours trawling the Internet looking for a solution, but to no avail.

I'm running Intrepid 64bit on a quad core Intel Q8200 @ 3Ghz, 2GB DDR3 800, and a PCIe GeForce 8800 GT 512.

I seem to have tried every possible combination of configuration:
[LIST]
[*]Options in xorg.conf: TripleBuffer, UseCompositeWrapper, DynamicTwinView Off
[*]Sync to VBlank and Flipping in nvidia-settings,
[*]Display Settings in CCSM,
[*]Compiz command-line options: --loose-binding, --indirect--rendering
[/LIST]

I have also tried several versions of the NVIDIA driver and I'm currently running the latest beta, 180.06.

However, when the Compiz Benchmark plugin is running, the tearing does not occur and the visuals appear very smooth.

I really hope someone can point me in the right direction here.

Thanks,
Andy

---

### Post by loomsen on 2008-12-01
Hello.

The newest beta is 180.08, which is working for me, tho not as I'm actually used to.

However, I'll just post my config, you may want to take a look at the threads in my signature concerning this issue.

First, you should enable direct rendering in compiz. Indirect rendering means that before an event is rendered, the actual event is parsed through Xorgs software rendering extension. This is equal to the DAMAGE Option, which should be enabled by default. 
The problem however is, that nvidia drivers ship with very restrictive permissions, only root will have permissions to access DRI (direct rendering infrastructure). How to grant permissions to other users you may find in my sig.


> Display Settings in CCSM

Well, which settings do you have specified then? 

I generated some custom modelines using cvt, which might be sth you'd want to consider too.

For instance, here's my xorg.conf (cut some irrelevant parts out as I'm using it on 2 Screens, my Laptop and my TV)

```

#####         LAYOUT:       ##########
################################################
####          OUTPUT        ####################
################################################
########## LAPTOP --- SCREEN ##
	#######################
	#  LAPTOP - GRAFIKKARTE  #
	##########################
	#  LAPTOP - MONITOR  #
	######################
######################################
#####         INPUT            ################
###############################################
	## INPUT - MOUSE ##
	## INPUT - TOUCHPAD ##
	## INPUT - KEYBOARD ##
####################################################
	# SERVER HINTS #
	################
Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
#	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	FontPath        "/usr/share/fonts/X11/misc"
	FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath        "/usr/share/fonts/X11/Type1"
	FontPath        "/usr/share/fonts/X11/100dpi"
	FontPath        "/usr/share/fonts/X11/75dpi"
	FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

####   OUTPUT    ####
#####################

Section "Device"
	Identifier     "Videocard0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8600M GT"
	BusID          "PCI:1:0:0"
	Screen          0
	Option		"ConnectedMonitor"	"DFP"
	Driver		"nvidia"
	Option		"TripleBuffer" "True"   [color=blue]#Only use with 256MB+ VRAM[/color]
#       Option          "DisableGLXRootClipping""True" [color=blue]#GL apps render to root window[/color]
#	Option          "DamageEvents"          "True" [color=blue]#Direct Rendering bypassing X-server[/color]
#	Option          "AddARGBGLXVisuals"     "True" [color=blue]#Default
#	Option          "RenderAccel"           "True" [color=blue]# FIXME: Modes EAX, XAA[/color]
	Option          "NoLogo"                "True"
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "DFP"
#	HorizSync       55.93
#	VertRefresh     60.0
# DEFAULT
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
	Modeline "1440x900"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
# REDUCED BLANK, COMPOSITE, INTERLACED
# 1440x900 119.56 Hz (CVT 1.30MA-R) hsync: 57.03 kHz; pclk: 91.25 MHz
#	Modeline "1440x900R"   91.25  1440 1488 1520 1600  900 903 909 954 composite interlace +hsync -vsync
# COMPOSITE, INTERLACED
# 1440x900 119.69 Hz (CVT 1.30MA) hsync: 58.17 kHz; pclk: 110.75 MHz
	Modeline "1440x900_60.00"  110.75  1440 1528 1672 1904  900 903 909 972 composite interlace -hsync +vsync
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Videocard0"
	Monitor        "Monitor0"
	Option         "UseEdidDpi"	"false"
	Option	       "DPI"	"96 x 96"
	Option         "Coolbits" "1"
	Option         "NoLogo" "true"
	DefaultDepth	24
	Option		"metamodes"	"1440x900 +0+0;1440x900_60 +0+0"
	SubSection "Display"
		Depth   24
		Modes	"1440x900_60"	"1440x900"
	EndSubsection
EndSection

## INPUT ##
###########

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	Option         "CoreKeyboard"
	Option         "XkbRules" "xorg"
	Option         "XkbModel" "pc105"
	Option         "XkbLayout" "de"
	Option         "XkbVariant" "nodeadkeys"
EndSection

## SERVER-FLAGS/-HINTS ##
#########################

Section "Extensions"
	Option         "RENDER" "true"
	Option         "DAMAGE" "true"
	Option		"Composite"	"enable"
EndSection

Section "Module"
	Load           "bitmap"
	Load           "ddc"
	Load           "extmod"
	Load           "freetype"
	Load           "int10"
	Load           "vbe"
	Load           "dbe"
	Load           "record"
	Load		"glx"
	Disable		"dri2"
EndSection


Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "DRI"
	Group 	"video"
	Mode 	0666
EndSection

```

But try and read my Howtos first as they probably will eliminate the main part of the problem.


*edit*

You may as well try and disable the PowerMizer, just read it works when the Benchmark-plugin is running. Try with Coolbits enabled, and set 3D Modes to max then in nvidia-settings. But if you do so, keep an eye on your Thermal Monitor as well.

---

### Post by _AndY on 2008-12-02
Hey, thanks for the reply.
I'll give that a go and see where it gets me.

But for now, I've upgraded to Compiz from git, which includes the Freely Transformable Windows plugin. For some reason, even when I'm not using any features of the plugin, my screen refreshes with every frame as if I were running the Benchmark plugin. For me this is an acceptable solution as I don't notice any difference in performance and my wobbly windows are incredibly smooth :)

Sorted, IMO :)

Andy

---

### Post by loomsen on 2008-12-02
Oh well, if you're pleased :) I however wouldn't be I guess ^^
Anyway, two things I just want to mention. If you're on Intrepid the restricted permissions of your driver still exist, preventing you from using your hardware properly.
So, at least I'd add the DRI Section to my xorg.conf if I was you, and add your user to the group video.
My sig points to a small Howto set it up. You may use GUI to add you to the proper group as well, but this will not loosen your permissions, so the xorg.conf Section is mandatory for this issue.

Just to compare, left without proper permissions, just created a user and imported the same profile as the one I use on the right pic, my base account with apropriate permissions:
[[img]http://www.ubuntu-pics.de/thumb/6682/screenshot_wo_dri_AUi7Zh.png[/img]](http://www.ubuntu-pics.de/bild/6682/screenshot_wo_dri_AUi7Zh.png) [[img]http://www.ubuntu-pics.de/thumb/6681/screenshot_22_PyHXfv.png[/img]](http://www.ubuntu-pics.de/bild/6681/screenshot_22_PyHXfv.png)

If you open up both shots next to each other it should get more clear. Sure, compiz will still work, but it will not as soon as you try and make use of your hardwares built-in 3D enhancement and antialiasing features. 

And, hence it's just 4 lines of text to add, this would & will always be the first thing I do after installing Intrepid (actually I do a lot since I help a lot of friends with their machines)

> I've upgraded to Compiz from git

Then you should grab protobuf. You'll notice a decent improvement in smoothness once the cache is built (takes about 2-5 min, depending on your CPU) This as well is explained in a Howto in my sig :)

---

### Post by _AndY on 2008-12-02
Nice howto :)
I added myself to the group and modified my xorg.conf. You'd think this would be set by default...

I also installed protobuf, although the tearing still occurs when that Compiz plugin isn't enabled.

I'm happy right now though as my system's still really fast, but prettier now too :)

Thanks again for your help,
Andy

---

