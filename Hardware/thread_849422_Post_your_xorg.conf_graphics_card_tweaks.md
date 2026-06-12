---
title: "Post your xorg.conf graphics card tweaks"
date: 2008-07-04
forum: Hardware
---

### Post by raul_ on 2008-07-04
Yesterday I was hunting for some tweaks for my intel driver, because OpenGL performance was very choppy. I eventually found some very good tips buried in the Gutsy archives. This lead me to the question "What if there was a place where these tips were centralized, so everyone can check them out?"

So here it is. 

**FIRST SOME GUIDELINES:**

-Post the name of the driver you are using (intel, nvidia, ati, catalyst, etc)
-Use the "Search this thread" in the "Thread Tools" menu, to check if your tip was already posted. **PLEASE DON'T DOUBLE POST TIPS**
-Use the "Search this thread" to check for specific tweaks for your driver.**DON'T USE THIS THREAD FOR BEGGING**

You will have to hunt them down. If there are 10 posts with your driver in it, you'll have to check them all.

[COLOR="Red"]**Important:**[/COLOR] These are just tips, my guess is that users won't be held responsible for whatever option they posted, that ended up frying your GPU (I'm just exagerating so you get the point)

---

### Post by raul_ on 2008-07-04
With that said, I guess I'll start. Here are some options that I think improved my opengl performance.

```

Driver      "intel"
Option      "AccelMethod" "XAA"
Option      "MigrationHeuristic" "greedy"
Option      "ExaNoComposite"     "false"
Option	    "TripleBuffer" "true"
Option      "Tiling"    "true"
Option	    "PageFlip"	"true"


```

---

### Post by diaa on 2008-07-27
I have an intel 915 GMA card and I was looking for ways to improve the performance of OpenGL, I'm using the *intel* driver(not the i810 driver).

Following [this guide]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%28Hardy_Heron%29_on_a_ThinkPad_T60#EXA_issues_with_intel_graphic_card_driver_.28945.2C_965.29"), I got 250 FPS improvement in glxgears(I'm aware it's not a proper benchmarking tool), from 600 to 850, here are the relevant options:

```

Option "AccelMethod" "EXA"
Option "ExaNoComposite" "false"
Option "MigrationHeuristic" "greedy"

```

I tried the last 3 options(Triplebuffer, Tiling and Pageflip) from your config file but I noticed no improvement or degradation in performance.

Update: 
1- I tried XAA but didn't get any improvement so I reverted to EXA as it's the newer method.
2- After some experiments and checking the man pages I found that the important settings that gave me this performance boost are
```

    Option      "MigrationHeuristic" "greedy"
    Option      "ExaNoComposite"     "false"

```

---

### Post by Naiki Muliaina on 2008-07-27
I take it this is just the device section? Only had to touch xorg once when i got this card so not realy familiar with it ^^ My internal card just used to work hehe.

Radeon HD 2400 pro AGP

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay"      "off"
        Option      "OpenGLOverlay"     "off"
        Option      "TexturedVideo"     "on"
EndSection

Used ATI's own driver. Sure i read this somewhere offical (like ATI's website), but with the HD series your meant to turn video overlay off and turn textured video on.

Thats mine ^^

---

### Post by markbuntu on 2008-07-27
This is wwith the ATI driver 8.7 and a HD3650 card.

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "DRI"
        Group       "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection


Important note, changes to xorg.conf when using the ati driver will be ignored. To get around this you need to type this command in a terminal:

```

sudo aticonfig --input=/etc/X11/xorg.conf 

```
to write the changes with aticonfig.

---

### Post by sv1cdn on 2008-12-16
Markbuntu hello again here!
I am using Radeon HD 3450 with Intrepid 8.10 Ubuntu. When I enable Visual effects (even medium) I get a feeling that the windows moving, scrolling etc are much slower! When I have none visual effects I have booming speed... Any idea? Your changes in xorg.conf will they work in Intrepid 8.10?
Take care.
Dennis.

---

### Post by splint-84 on 2009-03-25
>  Markbuntu hello again here!
I am using Radeon HD 3450 with Intrepid 8.10 Ubuntu. When I enable Visual effects (even medium) I get a feeling that the windows moving, scrolling etc are much slower! When I have none visual effects I have booming speed... Any idea? Your changes in xorg.conf will they work in Intrepid 8.10?
Take care.
Dennis. 

I've just tried those tweaks on 8.10 with the 9.2 restricted driver. Everything works fine so far, so at least it didn't break anything. Not sure if I've gained much speed though, but it did appear to fix the issues I was having while trying to play video...

---

### Post by FaizanKazi on 2009-04-21
So I installed the 8.59.2 drivers for my Ati Mobility x1400 the Ubuntu way (Restricted drivers manager).

boy does it feel weird to have an old driver. MESA drivers gave me ~660 fps with glxgears and ati drivers give me ~900 fps, but the mesa drivers felt a lot smoother and my display didnt get corrupted every single time i ran glxgears :s 

btw my xorg appears strangely empty: 

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

doesnt that seem a LITTLE short?
(i had previously installed the drivers using envyng and then uninstalled them using envyng, if that helps any)
EDIT: I am using Compiz fusion

---

### Post by Ekeluo on 2009-07-16
Intel GMA 900, not benchmarked.Running KDE4.3 RC2 effects smoothly though. My Xorg:

```
Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Wierd & short huh?! I did pin the drivers that worked for me (combo of future mesa & libdrm with older intel drivers). Addition of any extra lines (like option exa enable) usually results in gdm not being able to load, flickering cursor only. All good now though.

---

### Post by kingsleyben on 2009-08-18
I'm new to Linux.  Using Nvidia Drivers.  I can't get my resolution to stay where I want it.  Earlier today I changed it from "auto" to "1366x768" in system-preferences-display.
I clicked Save X Configuration File and got the error "Failed to parse existing X config file '/etc/X11/xorg.conf'!"  So everytime I rebooted, I would have to go change the resolution again.  Well, now when I change the resolution to "1366x768", my screen goes black and won't come back.  I have to reboot.  
Xorg file looks like this

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Virtual 2048 768
        EndSubSection
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
EndSection


I am afraid to edit it because I don't know what I'm doing.  My graphics card is a XFX Geforce 8800GS Alpha Dog Edition.  Mobo is [SIZE=2]eVGA nForce 680i SLI.  Any help would be GREATLY appreciated. I am a NOOB!
[/SIZE]

---

### Post by iyas120 on 2009-12-18
Hi all,

I am using HD2600xt. First i use this tutorial, following the manual installation in: 
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

at last step it became blank screen when using 
sudo aticonfig --initial -f 

I study the "xorg.conf" using "sudo gedit /etc/X11/xorg.conf" and all works by adding 1 line to set my monitor to use 1152x864 in the monitor section : Virtual 1152 864

the complete xorg.conf :


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 1152 864
	EndSubSection
EndSection

---

### Post by pi/roman on 2010-01-14
Configuration for Gateway MX3228 running VIA Unichrome Pro chip which I pieced together from many different sources.  Included are all the possible options for my vga controller which I am only using a few of.  OpenGL was not installed properly by default.  I had to update the 2 mesa packs, libgl1-mesa-glx and libgl1-mesa-dri, and also install and run the "driconf" tool and also include the load "dri" and load "glx" in the module section.  After correcting openGL, graphics and everything else in general began to run much smoother.
I could not get the 800x480 mode working.
Openchrome is the driver I am using.

```
Section "ServerLayout"
        Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
  Load         "dri"
  Load         "glx"
  Load         "dbe"
  Load         "extmod"
  Load         "dri2"
  Load         "record"
EndSection

Section "device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "PrintVGARegs"           # [<bool>]
        #Option     "PrintTVRegs"            # [<bool>]
        #Option     "I2CScan"                # [<bool>]
        #Option     "VBEModes"               # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # <str>
        #Option     "ExaNoComposite"         # [<bool>]
        #Option     "ExaScratchSize"         # <i>
        #Option     "SWCursor"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # [<str>]
        #Option     "VideoRAM"               # <i>
        #Option     "ActiveDevice"           # [<str>]
        #Option     "BusWidth"               # [<str>]
        #Option     "Center"                 # [<bool>]
        #Option     "PanelSize"              # [<str>]
        #Option     "ForcePanel"             # [<bool>]
        #Option     "TVDotCrawl"             # [<bool>]
        #Option     "TVDeflicker"            # <i>
        #Option     "TVType"                 # [<str>]
        #Option     "TVOutput"               # [<str>]
        #Option     "DisableVQ"              # [<bool>]
        #Option     "DisableIRQ"             # [<bool>]
        #Option     "EnableAGPDMA"           # [<bool>]
        #Option     "NoAGPFor2D"             # [<bool>]
        #Option     "NoXVDMA"                # [<bool>]
        #Option     "VbeSaveRestore"         # [<bool>]
        #Option     "DisableXvBWCheck"       # [<bool>]
        #Option     "MaxDRIMem"              # <i>
        #Option     "AGPMem"                 # <i>
    Identifier   "card0"
    VendorName   "VIA Technologies, Inc."
    Boardname    "S3 Unichrome Pro"
    Busid        "PCI:1:0:0"
    Driver "openchrome"
    Option "Monitor-LVDS"  "Integrated LCD"
    Option "PanelSize" "1280x768"
    Option "SWcursor"
    Option "EnableAGPDMA" "True" 
    Option "VBEModes"  "True"
EndSection

Section "monitor" 
    Identifier    "monitor0"
    Vendorname    "Gateway"
    Modelname    "SAMSUNG LCD MONITOR"
      Option       "DPMS"
      Option       "PreferredMode" "1280x768"
     DisplaySize  305 183
     HorizSync    30-62
     VertRefresh 43-60
    UseModes     "Modes0"
    Gamma    1.0
EndSection

Section "Modes"
  Identifier   "Modes0"
    Modeline "1280x768"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
    Modeline "800x480"  29.58  800 816 896 992  480 481 484 497  -HSync +Vsync
EndSection

Section "screen" 
    Identifier    "screen0"
    Device        "card0"
    Monitor       "monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth 24
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 16
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 15
        Modes "1280x768" "800x480"
    EndSubsection
    Subsection "Display"
        Depth 8
        Modes "1280x768" "800x480"
    EndSubsection
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection
```

---

### Post by eino1953 on 2010-01-14
I'm using a 42" TV as a monitor and, I would like to know If the following script would work.
I also have problems with permission to change the file.

 Section "Monitor"
Identifier "Monitor0"
VendorName "Sharp"
ModelName "LC-42SB45U"
HorizSync 30.0 - 83.0
VertRefresh 50.0 - 76.0
Option "DPMS"
EndSection

Section "Device"
Identifier "Device0"
Driver "intel"
VendorName "Intel 82865G"
EndSection

Section "Module"
Load "glx"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1080"
EndSubSection
EndSection

---

### Post by 1mrfab on 2010-03-30
Card: VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
1680x1050 mode added with help from xrandr

I where trying to 
```
aticonfig --query-monitor
```got the error Error: option --query-monitor is not supported when RandR 1.2 is enabled! so i used xrandr to add the resolution in catalyst control center this way
```
cvt 1680 1050
# 168x1050 59.52 Hz (CVT) hsync: 64.81 kHz; pclk: 14.00 MHz
Modeline "1680x1050_60.00"   14.00  168 176 192 216  1050 1053 1063 1089 -hsync +vsync

xrandr --newmode  "1680x1050_60.00"   14.00  168 176 192 216  1050 1053 1063 1089 -hsync +vsync
xrandr --addmode CRT1 "1680x1050_60.00"
```And to my big suprise the mode 1680x1050 was added in catalyst working finally for me

Section "ServerLayout"
   Identifier     "amdcccle Layout"
   Screen      0  "aticonfig-Screen[0]-0" 1680 0
   Screen         "amdcccle-Screen[1]-1" 0 24
EndSection

Section "Files"
EndSection

Section "Module"
   Load  "glx"
EndSection

Section "ServerFlags"
   Option       "Xinerama" "off"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Monitor"
   Identifier   "0-CRT1"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
   Option       "Disable" "false"
   Option       "PreferredMode" "1680x1050"
   Option       "TargetRefresh" "60"
   Option       "Position" "0 0"
   Option       "Rotate" "normal"
EndSection

Section "Monitor"
   Identifier   "0-DFP1"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
   Option       "PreferredMode" "1024x768"
   Option       "TargetRefresh" "60"
   Option       "Position" "0 0"
   Option       "Rotate" "normal"
   Option       "Disable" "false"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   Option       "UseFastTLS" "1"
        Option       "EnableRandR12" "false"
   Option       "Monitor-CRT1" "0-CRT1"
   Option       "Monitor-DFP1" "0-DFP1"
   BusID       "PCI:1:0:0"
EndSection

Section "Device"
   Identifier  "amdcccle-Device[1]-1"
   Driver      "fglrx"
   Option       "Monitor-CRT1" "0-CRT1"
   BusID       "PCI:1:0:0"
   Screen      1
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device     "aticonfig-Device[0]-0"
   Monitor    "aticonfig-Monitor[0]-0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection

Section "Screen"
   Identifier "amdcccle-Screen[1]-1"
   Device     "amdcccle-Device[1]-1"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection

---

### Post by Tosho on 2011-04-12
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 3.3.10524 Compatibility Profile Context

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x720"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1024x768"
	Option	    "TargetRefresh" "100"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-CRT1" "0-CRT1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Virtual 3200 1500
	EndSubSection
EndSection

```

I'm using my old CRT monitor with the VGA port of the laptop. Should be there that Option in Screen Section - Virtual "w" "h" or I have to remove it?
What extra Options I can add to tweak the card a little because when I play some game with wine it looks for me that the video is not using all it's "power".

---

