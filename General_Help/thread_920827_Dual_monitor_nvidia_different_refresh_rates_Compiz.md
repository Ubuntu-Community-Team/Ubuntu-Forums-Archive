---
title: "Dual monitor nvidia different refresh rates Compiz problem"
date: 2008-09-15
forum: General Help
---

### Post by asc2null on 2008-09-15
I'm having issues on nvidia card(64 bit platform) with dual monitors.  This is an hp tx1000 laptop.  One has a 60hz refresh and the external monitor has 75hz refresh.
The non-default screen when using scale or zoom has a glitchy looking diamond shaped pixalated blur which shows the skydome background from the cube.  Seems like some kind of refreshing errors.
Anyone with any ideas?

---

### Post by Sillywombat on 2008-09-15
Have you tried System>Aminitration>Nvidia server settings
should be able to change the refresh rate induvidualy for each screen. You may also want to check to see if your currently running up-to date drivers.
Hope this helps.

---

### Post by scorchgeek on 2008-09-15
Are you using desktop effects? If not, then you may not have the nvidia drivers. On my computer, I couldn't get dual monitors at all without it.

---

### Post by asc2null on 2008-09-16
I have the newest drivers and yes I've used nvidia-settings but I've also gone in and customized allot of things for my touchscreen and whatnot, my system isn't super linux friendly.
This isn't a newb question.The refresh rates are correct and individually set.
The problem seems to be with compiz-fusion and only when doing scale or zoom effect not with the cube.  It looks like either it doesn't have time to draw everything fast enough while its in motion or that compiz doesn't now to draw different screens at different rates.
I've also played with things like texture filter quality and making it less memory intensive hasn't helped.
Anyone trying this on a nvidia card without this affect?  what are your specs?

---

### Post by asc2null on 2008-09-17
So I've done a little more debugging it only occurs when the mouse is moving during an XGL event in compiz.

Here is my xorg.conf file
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "EETI"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "Corepointer"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "EETI"
    Driver         "egalax"
    Option         "Device" "usbauto"
    Option         "Parameters" "/var/lib/eeti.param"
    Option         "ScreenNo" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Chuntex CTX PV720"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync +vsync interlace
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    ModeLine       "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@85" 229.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@75" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine       "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine       "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine       "2048x1536@60" 266.9 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
    Gamma           1
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    Option         "RandRRotation" "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1280x800_60 +0+1024; CRT: NULL, DFP: 1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

	# 
    Identifier     "screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1280x800 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by sgarib on 2008-11-20
I have a similar problem, but a little more extensive. I also think this is due to a refresh rate problem. My system is an Ubuntu 8.10 amd64, with a correctly instaled nvidia driver. Because of a lack of my english, it is very hard for me to explain exactly what is happening, but whenever I rotate cube, or make a zoom of the desktop, I can see the screen "drawing itself" in the second monitor, with black thick lines appearing as the desktop moves, and then dissapear. This is not much of a problem but inhibe myself of bragging off about my OS!!

---

### Post by loomsen on 2008-11-21
You probably have specified your outputs and as well checked to force drawing independent outputs.

For me everything started working very smooth when I disabled the gconf backend integration and switched to flat file configuration. Give it a try, might work.

*edit*

@asc2null

You gotta specify your 2nd monitor in your server layout :) Otherwise this cannot work :)

Change your section to:
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
 [color=red]   Screen      1  "Screen1" RightOf "Screen0"[/color]
    InputDevice    "EETI"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "Corepointer"
    InputDevice    "Synaptics Touchpad"
EndSection

```

and your Screen1  section to:
```

Section "Screen"

	# 
    Identifier     "screen1"
[color=red]    Device         "Videocard1"[/color]
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1280x800 +0+0"
EndSection

```

You can delete the device0 and device1 sections as well, they aren't used at all.

Here's my xorg:
```

###############################################
	## INPUT - MOUSE ##
	## INPUT - TOUCHPAD ##
	## INPUT - KEYBOARD ##
################################################
####          OUTPUT        ####################
################################################
########## LAPTOP --- SCREEN ##
	#######################
	#  LAPTOP - GRAFIKKARTE  #
	##########################
	#  LAPTOP - MONITOR  #
	######################
########## FERNSEHER --- SCREEN ##
	##########################
	#  FERNSEHER - GRAFIKKARTE #
	############################
	#  FERNSEHER - MONITOR  #
	#########################
####################################################
	# SERVER HINTS #
	################

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Synaptics Touchpad"
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
    Load           "record"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "True"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizTwoFigerScroll" "True"
    Option         "VertTwoFingerScroll" "True"
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

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CPT"
    HorizSync       30.0 - 75.0
    VertRefresh     50.0
#    ModeLine       "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: builtin, VertRefresh source: builtin
    ###### FIXME #######
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "UseEdidDpi" "FALSE"
#    Option         "DPI" "96 x 96"
    Option         "AllowGLXWithComposite" "true"
#   Option	   "XAANoOffscreenPixmaps"
    Option         "AddARGBGLXVisuals" "true"
#    Option         "AllowIndirectPixmaps" "true"
    Option         "Coolbits" "1"
    Option         "NoLogo" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
#    Option         "UseEdidDpi" "false"
#    Option         "DPI" "96 x 96"
    Option         "TVStandard" "PAL-B"
#   Option		"PixmapCacheSize" "2500000"
    Option         "AllowGLXWithComposite" "true"
#   Option		"XAANoOffscreenPixmaps"
    Option         "AddARGBGLXVisuals" "true"
#    Option         "AllowIndirectPixmaps" "true"
    Option         "Coolbits" "1"
    Option         "NoLogo" "true"
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
    Option         "RENDER" "true"
    Option         "DAMAGE" "true"
EndSection

Section "DRI"
    Group		"video"
	Mode	0666
EndSection

```

At the beginning you see the layout and how it is constructed. Btw, I don't think RandRRotation is an Option which accepts true as a value... So delete this line from your videocard0 section as well.

typing:
```

cat /var/log/Xorg.0.log | grep EE
```
will show errors of your current xorg configuration,
```

cat /var/log/Xorg.0.log | grep WW
```
will show warnings.

---

