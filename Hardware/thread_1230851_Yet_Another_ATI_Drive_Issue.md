---
title: "Yet Another ATI Drive Issue"
date: 2009-08-03
forum: Hardware
---

### Post by two1stnamz on 2009-08-03
Hi All,

I have been wrestling with Ubuntu 9.04 for what seems like forever, trying to get my Sapphire Radeon 4830 to cooperate with Ubuntu. Basically, like most ATI users, I'm having issues with my GPU and visual effects. Even with them off, the PC just doesn't feel 100%. Here are's my system info:

CPU: Intel C2D 3.17Ghz
RAM: G.SKILL 2X2Gb
Mobo: Gigabyte UD3R
GPU: Saphire Radeon 4830

I've tried installing the opensource drivers, but they aren't much better. I currently have the latest proprietary drivers from ATI installed, and they seem to be a little more stable. When I downloaded, I built the package marked especially for Ubuntu and installed them.

fglrxinfo gives this:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series  
OpenGL version string: 2.1.8673

Attached is the output to glxinfo. Here is my xorg.conf file:
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load "dri"
        Load "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
        Option        "VideoOverlay" "on"
        Option        "OpenGLOverlay" "off"
        Option        "EnableRandR12" "false"
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
    EndSubSection
EndSection

When I type glxgears with effects turned off, here's what I get:
41316 frames in 5.0 seconds = 8263.055 FPS
41721 frames in 5.0 seconds = 8344.196 FPS
41671 frames in 5.0 seconds = 8334.070 FPS
41728 frames in 5.0 seconds = 8345.446 FPS

When I turn effects on, here's what I get:
15496 frames in 5.0 seconds = 3099.122 FPS
15677 frames in 5.0 seconds = 3135.359 FPS
15530 frames in 5.0 seconds = 3105.961 FPS
15203 frames in 5.0 seconds = 3040.596 FPS

Logging into Ubuntu with effects off takes roughly 5 seconds before the interface showes up, with effects on, between 20-25. I can go on and on, but I'll save it for..anways. Thanks in advance!

---

### Post by two1stnamz on 2009-08-03
UDPATE: I tried the solution from [Howto: Fix Ubuntu 9.04 ATI Driver Issues]("http://ubuntuforums.org/showthread.php?t=1229145") and I end up with the ATI driver not installing from the Hardware Drivers console, so basically now I'm back to pretty much a fresh install state with no drivers installed and intrepid settings.

---

### Post by two1stnamz on 2009-08-05
Anyone??? Any kind of direction would be much appreciated.

---

### Post by johntrottier on 2009-08-05
I wish I could say I have answers, but as you can see from my post, I have not had a lot of luck either. The one thing I am pretty sure of at this point is that the xorg.conf file does very little to help your situation and a great deal to hurt it. 
What I have seen is that my best approach to getting the proprietary driver to work has been:
Do a clean install - this wipes out the changes made in the kernel by various attempts at getting the driver to work.
Load the proprietary driver using the system>administration route
Once the driver is loaded and the machine rebooted, use add/replace programs to install the ATI Catalyst control center
Use this (and only this) utility to adjust the operation of your card.
Do not use the command line
Do not edit xorg.conf
Do not use any of the settings under preferences>screen resolution

This at least has resulted in a stable system for me. I don't know if it is the best approach, as it certainly flies in the face of the usual open Linux philosophy.  But I suspect that as long as ATI and NVidia are at war, they will not release any of their secrets, which means that open drivers will not have them, and the proprietary drivers will be closed and buggy, and will not play well with the open side of the system.

Ahhh - technology is great - when it works

---

