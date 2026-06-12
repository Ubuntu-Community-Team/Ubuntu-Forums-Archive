---
title: "Failed to Parse.... cannot save nvidia-settings"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Jock McJock on 2009-04-25
Ubuntu 9.04 NEW install Amd 2400 512mb GeForce4 MX 440



1. sudo apt-get install envyng-core
2. sudo envyng -t
3. installed 96.43.10-0ubuntu1.1
4. rebooted system/administration/hardware drivers/ 
Checked this driver is installed and currently in use.



Enter "sudo or gksudo nvidia-settings" and tweak settings click on save and...........
Error message appears and it exits nvidia-settings.


"Failed to Parse" cannot save nvidia-settings. 

 
 

PARSE ERROR:  Parse error on line 41 of section Module in file /etc/X11/xorg.conf.
"Disable" is not a valid keyword in this section. Segmentation fault



Is there anything missing from the xorg.conf file, Ubuntu 8.10 xorg.conf TVOUT colour runs fine with the xorg.conf file below, so I copied over some lines from it to get TVOUT colour on Ubuntu 9.04. Is this a bug or is there a simple tweak needed to the xorg.conf file to enable save in the nvidia-settings menu.  tia...



UBUNTU 9.04 xorg.conf 

Section "Monitor"
	Identifier	"Configured Monitor"
        ModelName       "CRT-0"
	HorizSync       30.0 - 70.0
	VertRefresh     60.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
        Option         "TwinView" "1"
        Option         "TwinViewXineramaInfoOrder" "CRT-0"
        Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: 1024x768 +0+0"
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce4 MX 440"
Option "TVStandard" "PAL-I"
Option "TVOutFormat" "COMPOSITE"
EndSection




UBUNTU 8.10 xorg.conf 

Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       30.0 - 70.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440"
Option "TVStandard" "PAL-I"
Option "TVOutFormat" "COMPOSITE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, TV: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

---

### Post by LitusMayol on 2009-04-27
Hey bro,

I'm having the same problem.Identic one! But in line 29 instead yours.

---

