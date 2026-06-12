---
title: "Problems with xinerama in intrepid ibex."
date: 2008-11-15
forum: General Help
---

### Post by alternotgoto on 2008-11-15
Hi all, I am tearing my hair out with this, and am thinking of moving back to hardy, because I know that works.

OK here is the problem. I have 3 screen display machine using two NVidia cards. One has a VGA and DVI and the other 2 VGAs. I am working with monitors plugged into the VGA and DVI card and just one of the VGAs on the other card.

I am on intrepid ibex fully up to date.

Anyway I can get X to boot, but only without Xinerama disabled. If I enable Xineram then X starts, crashes with absolutely no messages in /var/log/Xorg.0.log at all. (which is down-right weird and not something I have seen before).

Anybody got any ideas?

Attaching the Xorg.conf for your perusal.

P.S this is my wife's machine, she has reverted to using my Windows XP laptop at the mo' because I can't get her desktop working (constantly swearing at it in the study)

---

### Post by alternotgoto on 2008-11-15
Looks like the attachment didn't work, so here is the xorg.conf in full.

<-----start cut here----------->
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
    Identifier  "Monitor[0]"
    HorizSync   31.5 - 50.0
    VertRefresh 40-90
EndSection

Section "Monitor"
    Identifier  "Monitor[1]"
    HorizSync   31.5 - 50.0
    VertRefresh 40-90
EndSection

Section "Monitor"
    Identifier  "Monitor[2]"
    HorizSync   31.5 - 50.0
    VertRefresh 40-90
EndSection

Section "Device"
    Identifier  "Device[0]"
    Driver      "nvidia"
    BUSId       "PCI:1:0:0"
    Screen      0
    Boardname	"NV44 [GeForce 6200 LE] (rev a1)"
    Vendorname  "nVidia Corporation"
EndSection

Section "Device"
    Identifier  "Device[1]"
    Driver      "nvidia"
    BUSId       "PCI:1:0:0"
    Screen	1
    Boardname	"NV44 [GeForce 6200 LE] (rev a1)"
    Vendorname  "nVidia Corporation"
EndSection

Section "Device"
    Identifier  "Device[2]"
    Driver      "nvidia"
    BUSId       "PCI:2:18:0"
    Boardname	"NV34 [GeForce FX 5200] (rev a1)"
    Vendorname  "nVidia Corporation"
EndSection

Section "Screen"
    Identifier  "Screen[0]"
    Device      "Device[0]"
    Monitor     "Monitor[0]"
    DefaultDepth 24
    Subsection "Display"
        Depth       8
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen[1]"
    Device      "Device[1]"
    Monitor     "Monitor[1]"
    DefaultDepth 24
    Subsection "Display"
        Depth       8
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen[2]"
    Device      "Device[2]"
    Monitor     "Monitor[2]"
    DefaultDepth 24
    Subsection "Display"
        Depth       8
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "ServerLayout"
   Identifier  "Default"

    Screen 0 "Screen[0]"
    Screen 1 "Screen[1]" RightOf "Screen[0]"
    Screen 2 "Screen[2]" RightOf "Screen[1]"
    InputDevice "ConfiguredMouse" "CorePointer"
    InputDevice "GenericKeyboard" "CoreKeyboard"

EndSection

Section "ServerFlags"
#    This flag is causing problems on intrepid ibex
#	Option "Xinerama" "true"
EndSection
<-----end cut here------------->

---

### Post by alternotgoto on 2008-11-19
Well I have given up with this. It is definitely a problem with the version of X. In particular xinerama

I can 3 screens to come up separately, so I don't believe it is the video drivers (good old proprietary nvidia) but once I try and use Xinerama, then X just crashes.

I tried this with and without compiz installed, 32 and 64 bit versions of intrepid, but no joy.

I have reverted to 64 bit hardy, which works.

I think this is a bug in X. Anybody got any idea on how to report this?

Many thanks,

---

