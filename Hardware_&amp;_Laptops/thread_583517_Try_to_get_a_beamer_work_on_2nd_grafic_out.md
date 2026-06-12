---
title: "Try to get a beamer work on 2nd grafic out"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by 2beers on 2007-10-20
I need to get a propper setting for my beamer - wich is plugged into the 2nd grafic out port.

System:
OS: Ubuntu 7.10
Grafics: Nvidia 7500gt (restricted driver installed)
Monitor1:CRT  V7 S98S (automatically detected correctly)
Monitor2: Beamer (DLP) Medion. (automatically detected @ 640x480)

What i tried so far:
1.
Edit the xorg by hand (as i used to under feisty). Unfortunatley - as soon as i restart X to get the new settings to work, the all new automatic bulletproof just overrides my xorg with a new - not working - xorg.
2.
Made my own *.inf file - as the new "monitor and grafics" settings offer the use of such files.
After X restart: Same resault as above + grafic cards failure - falls back to vesa (or mesa?) driver.

Beamer specs:
Max (native) res: 1280x720
H-sync: 15,75 - 91,1 Hz
V-sync: 43 - 85 Hz 

How can i force the new X to accept my settings?

Atm i turn on the PC with the CRT plugged in only. Then i pluggin the beamer instead and it works. But actually thats not a sollution - especially - when i i.e. launch a game (=> x restart) the beamer will be detected - with wrong settings again.

---

### Post by 2beers on 2007-10-21
*push*

---

### Post by 2beers on 2007-10-22
Noone - i mean NO ONE?
May one at least confirm that problem?
I recently tried a different monitor setup (new TFT) - same problem.
Yet it's a very unknown brand - just an ASUS - wich doesn't appear in ubuntu's brand list.
It's not possible to chose the proper (native) res - wich would be 1650x1080.

Meanwhile i managed to get proper inf files (in my first attempt i made two " too much).

When using ONE inf file for the beamer, at least i can use the "clone" modus.
Not the "extended desktop" though.

Furthermore - when i use both inf files, one is just ignored (falls back to standard=wrong settings)

Guys - please i can not be the only guy on this planet with ubuntu using two monitors????

---

### Post by buellman on 2007-10-22
Hi,

as I am looking for the same thing you might want to have a look [here]("http://gentoo-wiki.com/HOWTO_Dual_Monitors").
I didn't try this howto so far (no time) but maybe it is a good starting point for investigations on this topic.

Greets. Buellman

---

### Post by 2beers on 2007-10-22
Thanks for the reply!

As i menationed in my 1st post, i allready edited my xorg by hand - with settings i used under feisty.
Unfortunatly gutsy just creates a new (wrong) xorg as soon as i restart X.
So i am afraid the link you provided, can't solve this problem :-/

---

### Post by pikmaster on 2007-12-27
I had the similar (same?) problem and I solved it by adding the following options to my xorg.conf file:


Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
        Option  "ConnectedMonitor"      "DFP-0,CRT-0"
        Option  "UseDisplayDevice"      "DFP-0,CRT-0"
        Option  "TwinView" "true"
        Option  "TwinViewOrientation"   "Clone"
        Option  "TwinViewXineramaInfoOrder"     "DFP-0,CRT-0"
        Option  "MonitorLayout" "LFP,LFP+CRT"
        Option  "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
EndSection


This is because X server does not detect the second display at the start and you have to force him to think the second display IS there. Without this, and using nvidia-settings I was able only to set the detected  display at 640x480 or 320x200.

---

### Post by diego-poa on 2008-07-20
> **pikmaster said:**
> I had the similar (same?) problem and I solved it by adding the following options to my xorg.conf file:


Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
        Option  "ConnectedMonitor"      "DFP-0,CRT-0"
        Option  "UseDisplayDevice"      "DFP-0,CRT-0"
        Option  "TwinView" "true"
        Option  "TwinViewOrientation"   "Clone"
        Option  "TwinViewXineramaInfoOrder"     "DFP-0,CRT-0"
        Option  "MonitorLayout" "LFP,LFP+CRT"
        Option  "metamodes" "DFP-0: 1024x768 +0+0, CRT-0: 1024x768 +0+0; DFP-0: 1280x1024 +0+0, CRT-0: 1280x1024 +0+0; DFP-0: 1024x768 +0+0, CRT-0: NULL"
EndSection


This is because X server does not detect the second display at the start and you have to force him to think the second display IS there. Without this, and using nvidia-settings I was able only to set the detected  display at 640x480 or 320x200.
Pikmaster, thank you very much!! I was almost giving up of linux, but your xorg.conf resolved all my problems!! I have to edit somethings manually and using nvidia-settings to adapt the xorg.conf to my machine. Because your xorg.conf puts me in a screen wider than mine, very strange. So I change it for 1280x800, here is the final xorg for curiosity, the nvidia-settings made some changes... take a look!

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Configured Mouse" "CorePointer"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
    Load           "record"
    Load           "xtrap"
    Load           "extmod"
    Load           "dri"
    Load           "dbe"
    Load           "type1"
    Load           "freetype"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "abnt2"
    Option         "XkbLayout" "br"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"

# jesli nei ustawisz mu na sztywno monitora (ConnectedMonitor) to bedzie dawal dla podlaczonego projektora jedynie rozdzielczosc 640x480. Do czasu az nie zrestartujesz X-ow z podlaczonym projektorem
# Removed Option "TwinView" "true"
# Removed Option "TwinViewXineramaInfoOrder" "DFP-0,CRT-0"
# Removed Option "metamodes" "DFP-0: 1280x800 +0+0, CRT-0: 1280x800 +0+0; DFP-0: 1280x960 +0+0, CRT-0: 1280x960 +0+0; DFP-0: 1280x800 +0+0, CRT-0: NULL"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
    Option         "ConnectedMonitor" "DFP-0,CRT-0"
    Option         "UseDisplayDevice" "DFP-0,CRT-0"
    Option         "TwinViewOrientation" "Clone"
    Option         "MonitorLayout" "LFP,LFP+CRT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x800_60 +0+0, DFP: 1280x800 +0+0; CRT: NULL, DFP: 1280x800 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by tad1073 on 2008-07-20
I am trying to get a dual head also. My first monitor is a LG Flatron L22WTG and my second monitor is a Samtron 75E. Any suggestions.

---

