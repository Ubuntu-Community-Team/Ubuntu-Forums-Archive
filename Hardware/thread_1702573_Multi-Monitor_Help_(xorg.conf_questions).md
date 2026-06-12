---
title: "Multi-Monitor Help (xorg.conf questions)"
date: 2011-03-08
forum: Hardware
---

### Post by brent_watson on 2011-03-08
Hopefully someone can help...

I've been messing with xorg.conf for 2 days trying to get a 3-Monitor setup working.  No luck.

Info:
-Using 2 ports from a ATI Radeon HD5570 card.
-Using 1 port from On Board graphics.
-I have "SurroundView" enabled in the BIOS which should let me do this.
-Info for cards from lspci:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
02:00.0 VGA compatible controller: ATI Technologies Inc Device 68d9
-I downloaded the latest ATI driver (fglrx) driver directly from ATI.  Version 10.10 I think.
-Ubuntu version 10.04.

Messing with xorg.conf I've been able to get stuff showing up on the On Board monitor OR on the PCI card monitors, but never both.

Below is my current xorg.conf file.  Which this, when booting, grub shows up on the On Board monitor, then once X starts, I get the login screen (and gnome) only on the 2 monitors connected to the PCI Card (the HD5570 card) and the On Board monitor gets stuck on the "Ubuntu..." loading screen.  (Note: If I hit Ctrl+Alt+F6 to get to TTY, it shows up on the OnBoard Monitor and the 2 monitors on the PCI card go blank).


If anyone with some Xorg knowledge could give me a hand, that would be AWESOME!

xorg.conf:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "screenA" 0 0
	Screen      1  "screenB" LeftOf "screenA"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
EndSection

Section "Monitor"
	Identifier	"philips1"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
EndSection

Section "Device"
	Identifier  "CardDevice"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "OnBoardDevice"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "screenA"
	Device     "CardDevice"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 1920
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screenB"
	Device		"OnBoardDevice"
	Monitor		"philips1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by djahma on 2011-06-10
Hi there,

Similar problem with me except both screen are showing 2 different desktops and one has no window manager etc.
Similar to Brent_Watson I've got one port on onboard graphics (Radeon 3000) and another one on GPU port ATI HD 5450.
> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 3000 Graphics
OpenGL version string: 3.3.10750 Compatibility Profile Context

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5450
OpenGL version string: 4.1.10750 Compatibility Profile ContextI've followed various tutos and installed the driver from ATI website, sorted ATI lags but I can't manage to get one desktop extended over the 2 screens. Each screen shows its own individual desktop: "Single  display desktop (multi-desktop)". The "Big desktop" option is not available in amdcccle.
I tried xinerama to pass windows from one to the other, but when on, it prevent the system to reach the login screen and all I seem to be able to do is ctrl+alt+F1 and type sudo aticonfig --xinerama=off to recover. 

The xorg.conf looks wrong to me because the screens or monitors do not seem to come together, they look pretty much independent; but I'm not good enough to find out what to change in it:confused::
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 1920 30
    Screen         "amdcccle-Screen[2]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "DesktopSetup" "horizontal"
    Option        "UseFastTLS" "1"
    BusID       "PCI:1:5:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "1-CRT2"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-0"
    Device     "amdcccle-Device[2]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```So ideally, I'm looking to get gnome panels on the HD5450 pulgged-in screen and get an extension of the same desktop on the onboard graphics connected screen. 

Any X11 fluent guy out there?:rolleyes:

Cheers

---

### Post by djahma on 2011-06-12
Ok, I went to the market place in despair and found a 1€ HDMI cable from a Rom there. Then plugged both my screens on the HD5450 card, changed BIOS setup to resort to the graphics card as a primary display, booted in console mode, typed $ sudo aticonfig --initial=dual-head -f; got an error, rebooted, typed the command again (went fine this time), then $ sudo vi /etc/ati/amdpcsdb, added the line EnableRandR12=Sfalse, then $ sudo vi /etc/X11/xorg.conf, added the line "EnableRandR12" "false" to both "device" sections, rebooted, and then I could change my setup to a "big desktop" in amdcccle!

Pfff, success wasn't easy to acheive!

btw, RandR12 is still enabled in spite of the added line, but it doesnt seem conflictual...I'll leave it there.

Good luck to you

---

### Post by BFG on 2011-06-23
I have a similar problem.  Any chance you could share the finished conf file? :)

---

### Post by djahma on 2011-06-23
> **BFG said:**
> I have a similar problem.  Any chance you could share the finished conf file? :)

There you go:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 10"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    Option        "Monitor-DFP2" "0-DFP2"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    Option        "EnableRandR12" "false"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3600 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

