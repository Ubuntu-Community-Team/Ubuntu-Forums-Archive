---
title: "Dual screen setup fails with blank monitors. help please."
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by codemills on 2005-06-03
i apt-getted fglrx and things and did fglrxconfig... then got XF96config file in /etc/X11 ....so i merged the contents of XF86.... to xorg.conf and corrected the errors i kept getting... until... 
Now ... i dodnt get any error message but a blank screen.

the comp boots and when gdm needs to start my monitors just show black screen .. nothing happens.. cant even switch between terminals by ctrl+alt+F1 F2 and so on.

i am attaching my xorg.conf ... mayb u can see something i cant see ... 

Regards,
Anshuman.
here comes the xorg.conf with fglrx merge.
```


Section "Files"
          RgbPath	"/usr/X11R6/lib/X11/rgb.txt"
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
SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
#         Option "AutoRepeat" "500 30"          
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

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   31.5 - 60.0
    VertRefresh 50 - 70
    Option "DPMS"
 #Modeline "800x600@60" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
 #Modeline "1024x768@60" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
EndSection


Section "Monitor"
    Identifier  "Monitor1"
    HorizSync   31.5 - 60.0
    VertRefresh 50 - 70
    Option "DPMS"
 #Modeline "800x600@60" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
 #Modeline "1024x768@60" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 0"
    Driver                              "fglrx"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "31.5 - 60.0" 
    Option "VRefresh2"                  "50 - 70" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "no"     
    Option "TVStandard"                 "PAL-B"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
    Option "Capabilities"               "0x00000000"
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
    BusID "PCI:2:0:0"    # vendor=1002, device=4151
    Screen 0
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 1"
    Driver                              "fglrx"
    BusID "PCI:2:0:0"    # vendor=1002, device=4151
    Screen 1
EndSection


Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter connector 0"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter connector 1"
    Monitor     "Monitor1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1024x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection
Section "ServerLayout"
    Screen "Screen0"
    Screen "Screen1" LeftOf "Screen0"
        InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


Section "DRI"
	Mode	0666
EndSection

```

---

### Post by codemills on 2005-06-03
now... after intensive googling i got to this blogpage [http://quark.humbug.org.au/blog/index.cgi/geek/linux/20050123094634.html](http://quark.humbug.org.au/blog/index.cgi/geek/linux/20050123094634.html) and modified my xorg.conf to this.



```
# Define both outputs on the card
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 1"
        Driver          "ati"
        BusID           "PCI:2:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 2"
        Driver          "ati"
        BusID           "PCI:2:0:0"
        Screen          1
EndSection

# Define both monitors
Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-60
        VertRefresh     50-75
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 2"
        HorizSync       30-60
        VertRefresh     50-75
        Option          "DPMS"
EndSection

# Define screens
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 1"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 2"
        Monitor         "Generic Monitor 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

# Now put it all together
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Default Screen"
        Screen          1 "Second Screen" LeftOf "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option "Xinerama"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

and finally i got DUAL/Extended mode running here \:D/  .  soo soo happy. 

But..... one slight thing happening... the gnome screen load on my right monitor (dvi) and extended/other screen on left monitor. (17" vga monitor)... now i want to reverse this thing. any help?
Note:- doing Screen          1 "Second Screen" LeftOf "Default Screen" or Screen          1 "Second Screen" RightOf "Default Screen" has no effect.


 :neutral: hope i pull through this last glitch too. wish me luck.

---

### Post by shakin on 2005-06-03
This could be the problem. You don't need the zero and one on these two lines:
```

Screen          "Default Screen"
Screen          "Default Screen" RightOf "Second Screen"

```

You also may or may not want to turn on Xinerama (also in ServerLayout):
```

Option 		"Xinerama" 	"On"

```

---

### Post by codemills on 2005-06-05
just wanted to tell everything is sorted out and nothing much has changed in the above discussed config, :D

here is the result

[[img]http://img215.echo.cx/img215/2906/smallduallinuxclean0mu.png[/img]](http://img215.echo.cx/img215/3606/bigduallinuxclean9fi.png)

[[img]http://img215.echo.cx/img215/1805/smallduallinuxbusy0hr.png[/img]](http://img215.echo.cx/img215/300/bigduallinuxbusy9gm.png)

peace,
Anshuman.

---

### Post by optik on 2005-06-05
[QUOTE=codemills]just wanted to tell everything is sorted out and nothing much has changed in the above discussed config, :D

here is the result

[[img]http://img215.echo.cx/img215/2906/smallduallinuxclean0mu.png[/img]](http://img215.echo.cx/img215/3606/bigduallinuxclean9fi.png)

[[img]http://img215.echo.cx/img215/1805/smallduallinuxbusy0hr.png[/img]](http://img215.echo.cx/img215/300/bigduallinuxbusy9gm.png)

peace,
Anshuman.[/QUOTE]
 Please could you post your exact xorg.conf.... I am haveing the same problem as you, it would be much appreciated.....

thanks

David

---

### Post by codemills on 2005-06-05
[QUOTE=optik]Please could you post your exact xorg.conf.... I am haveing the same problem as you, it would be much appreciated.....

thanks

David[/QUOTE]
here it comes ...  :)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
          RgbPath	"/usr/X11R6/lib/X11/rgb.txt"
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
SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
#         Option "AutoRepeat" "500 30"          
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

# Define both outputs on the card
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 1"
        Driver          "ati"
        BusID           "PCI:2:0:0"
        Screen          1
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 2"
        Driver          "ati"
        BusID           "PCI:2:0:0"
        Screen          0
EndSection

# Define both monitors
Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       30-60
        VertRefresh     50-70
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor 2"
        HorizSync       30-60
        VertRefresh     50-70
        Option          "DPMS"
EndSection

# Define screens
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 1"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 (RV350 AS) Head 2"
        Monitor         "Generic Monitor 2"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

# Now put it all together
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen         0 "Default Screen"
        Screen         1  "Second Screen" LeftOf "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option "Xinerama"
#	Option "Xinerama" "On"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by optik on 2005-06-05
For some reason, the conf works but.... My displays run at 1280x1024 (optimal) even when I add 1280x1024 as a mode line it does not function properly, it runs at 1024x768.

When I remove all other modelines to leave **ONLY** 1280x1024 then it runs as a random resolution!

What the hell is wrong here!?

---

### Post by codemills on 2005-06-05
[QUOTE=optik]For some reason, the conf works but.... My displays run at 1280x1024 (optimal) even when I add 1280x1024 as a mode line it does not function properly, it runs at 1024x768.

When I remove all other modelines to leave **ONLY** 1280x1024 then it runs as a random resolution!

What the hell is wrong here!?[/QUOTE]
 interesting.
well lets say linux works in mysterious ways :P

but alteast it works some way or other. i too have kept myself satistfied with dual running and no acceleration. oh well. lets hope ati get their heads right and do something bout this.

---

### Post by optik on 2005-06-05
[QUOTE=codemills]interesting.
well lets say linux works in mysterious ways :P

but alteast it works some way or other. i too have kept myself satistfied with dual running and no acceleration. oh well. lets hope ati get their heads right and do something bout this.[/QUOTE]

The only problem is that I **CANT** use it as it is... i've had to resort to using one monitor for the time being as Id rather have one at 1280x1024 than one at 1024x768....

---

### Post by optik on 2005-06-06
Sorry to bump this early but please help me.... I have trawled the forums and cant find a solution.....

---

### Post by codemills on 2005-06-06
optik u got everyright to bump this thread. man we need to do something.
i m so angry i want to grab balls of the person responsible at ati for making drivers and installation thing.

i am pming u

---

