---
title: "Nvidia 8600GT driver makes my Philips 170S LCD monitor look &quot;blurry&quot;"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by hazica on 2008-04-13
Hi everyone!

I just bought some new hardware after my old mainboard croaked, I did a fresh install of Kubuntu and everything worked pretty well. The first time I booted up the new system, I was asked whether I wanted to install the restricted Nvidia driver. I did and I rebooted after the successful installation.

Now, the problem is that the screen doesn't look quite as "clean" as it did before. By clean I mean that the fonts aren't properly anti-aliased and neither are the other visual elements of my desktop; images also suffer from this slight distortion of the edges.

I tried playing with nvidia-settings but it was without any results. When I go back to the default Ubuntu driver, everything looks nice and smooth, but the PC is way too slow. So I think that the problem might lie with the restricted driver. (I also tried installing this driver straight from the Nvidia website. No improvements here either.)

In nvidia-settings, my monitor, a Philips 170S is called CRT-0. Perhaps that's the problem...?
I also have a TV hooked up the the graphics card, which I use in "twinview" mode.

Also, here's my xorg.conf:

```


Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "deadgraveacute"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Philips 170S"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Philips 170S"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nv"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Philips 170S"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    Option	   "FlatPanel" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, TV: nvidia-auto-select +0+128; CRT: 1024x768 +0+0, TV: nvidia-auto-select +0+0; CRT: 800x600 +0+0, TV: nvidia-auto-select +0+0; CRT: 640x480 +0+0, TV: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```


Any suggestions?

Thanks.

EDIT: forgot something: the Option "FlatPanel" "true" is something I tried after reading some similar posts. (it had no effect whatsoever...)

---

### Post by hazica on 2008-04-14
Nothing, anybody?

I'd really appreciate your help folks!

Sorry for bumping this post but... I am quite desperate here. I can't stand looking at this awful  screen.

Thanks.

---

