---
title: "ATI9100GP dualhead (Gutsy = SADNESS)"
date: 2008-05-10
forum: Hardware
---

### Post by bohsocks on 2008-05-10
I know a lot of people have issues with this.... and I've searched... I just think that each issue can be so unique due to card-type and what exactly they want in a second monitor.... 

Most of the time my posts on here go unanswered.... PLEASE HELP :(

I have an HP laptop with VGA-Out and an ATI card.... it worked fine to connect my laptop to my TV through MergedFB in feisty.....

There are a number of reasons I want to upgrade from Feisty to Gutsy (Trevino's repo is half-dead, ipod-convenience for my iPhone, compiz ccsm, etc.) but when I do I lose my MergedFB obviously... and cannot figure out how to get my dual-monitors back.

Since my card is pre-9500, fglrx doesn't work for me.....

When I have my VGA cable connected (to my new Vizio with a RGB(VGA) input.... Xrandr doesn't recognize it as being connected..... 

I have had no success editing my xorg.conf on my own... because I have no idea what I'm doing... but I'm hoping that's the key to getting this to work.....

Here is my current xorg.conf:
> 
Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


Here is what I have tried:
> 
Section "Device"
    Identifier  "radeon0"
    Driver      "ati"
    BusID       "PCI:1:5:0"
    Screen 0
EndSection

Section "Device"
    Identifier  "radeon1"
    Driver      "ati"
    BusID       "PCI:1:5:0"
    Screen 1
EndSection

Section "Monitor"
    Identifier  "monitor0"
    Option      "DPMS"
EndSection

Section "Monitor"
    Identifier  "monitor1"
    Option      "DPMS"
EndSection

Section "Screen"
    Identifier  "screen0"
    Device      "radeon0"
    Monitor     "monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth       1
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       8
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       15
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       16
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes       "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier  "screen1"
    Device      "radeon1"
    Monitor     "monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth       1
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       4
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       8
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       15
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       16
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes       "1368x768" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "screen0"
    Screen      "screen1" RightOf "screen0"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"

    # Don't forget xinerama!!!111oneoneone11!eleven!!11
    Option "xinerama" "on"
    Option "clone" "off"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


Here are some of the edits I've tried... to no success!!!!!
> 
Section "Device"
    Identifier  "radeon0"
    Driver      "ati"
    BusID       "PCI:1:5:0"
    Screen 0
EndSection

Section "Device"
    Identifier  "radeon1"
    Driver      "intel"
    BusID       "PCI:1:0:0"
    Screen 1
EndSection

Section "Monitor"
    Identifier  "monitor0"
    Option      "DPMS"
EndSection

Section "Monitor"
    Identifier  "monitor1"
    Option      "DPMS"
EndSection

Section "Screen"
    Identifier  "screen0"
    Device      "radeon0"
    Monitor     "monitor0"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1280x800"
    EndSubSection
EndSection

Section "Screen"
    Identifier  "screen1"
    Device      "radeon1"
    Monitor     "monitor1"
    DefaultDepth    24
    SubSection "Display"
        Depth       24
        Modes       "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "screen0"
    Screen      "screen1" RightOf "screen0"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"

    # Don't forget xinerama!!!111oneoneone11!eleven!!11
    Option "xinerama" "on"
    Option "clone" "off"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


---

### Post by bohsocks on 2008-05-10
Bump

---

### Post by bohsocks on 2008-05-11
Shove

---

### Post by bohsocks on 2008-05-11
P-p-push

---

### Post by bohsocks on 2008-05-11
This forum is useless.

---

