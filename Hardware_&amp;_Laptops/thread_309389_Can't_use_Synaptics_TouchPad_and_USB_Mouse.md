---
title: "Can't use Synaptics TouchPad and USB Mouse"
date: 2006-11-29
forum: Hardware &amp; Laptops
---

### Post by birchwood on 2006-11-29
Hi. I have a very simple wish: for my touchpad to function as a touchpad, and for my standard USB mouse to operate as a standard USB mouse.

After a clean install, Edgy does not detect a touchpad. My xorg.conf indicates that the generic "mouse" driver is used. In this case, both my external USB mouse and my touchpad function, but I cannot use any of the additional functionality provided by the Synaptics driver (scrolling, accidental tap detection, etc.)

If I configure the device section for the mouse to use the "synpatics" driver, my touchpad works wonderfully, with all the extra functionality. However, my external USB mouse ceases to operate.

The next thing I've done was to try and define separate entries in xorg.conf for my touchpad and my USB mouse. I do know that my touchpad is **/dev/input/mouse0** and that my external USB mouse registers as **/dev/input/mouse1**. I've tried many different combinations, but I simply cannot get both pointing devices to work simultaneously, the touchpad as touchpad and the external USB mouse as a standard, external USB mouse.

Here is the relevant section in my current xorg.conf. As you can see, I've tried to define the touchpad as /dev/psaux, but I've also tried other possibilities. Right now, the touchpad doesn't work at all, and the USB mouse works normally.

> Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "TouchPad"
        Driver          "synaptics"
#       Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "SHMConfig"             "true"
EndSection


Thanks for the help!

---

### Post by birchwood on 2006-11-29
Fixed independently. To duplicate the input device section, I merely copied the one for the standard mouse. Unfortunately, both were defined as CorePointers, which xorg.conf doesn't like.

---

### Post by annda on 2006-11-29
here's my part of xorg.conf - and it works, even 2 mice connected at the same time. the mouse parts seem to be identical, but maybe the touchpad protocol option is the problem. also, i've never needed horizontal scrolling - maybe it should be set to "1" for full functionality.

i hope this helps.

```
Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection
```

---

### Post by finferflu on 2006-11-29
You just need to adjust your ServerLayout section. This is the relevant bit from my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

.......

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard" "CoreKeyboard"
	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice	"Synaptics Touchpad" "AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection
```

Then just restart your session, and it should work. 

I hope it helps! ;)

---

### Post by ubrox on 2008-03-24
ok ... I changed USB to be CorePointer and Synaptics to AlwaysCore.

If synaptics is set as CorePointer, USB does not work. If I set USB to CorePointer, synaptics wont work. 

How can I make both work at the same time?

Even if I unplug USB ... synaptics wont work.

Here is xorg.conf:

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Synaptics Touchpad" "AlwaysCore"
    InputDevice    "USB Mouse" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "true"
EndSection


Section "InputDevice"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "Auto"
        Option          "ZAxisMapping"          "4 5"
    Identifier     "USB Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Acer AL1916W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6100"
    BusID          "PCI:0:5:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6100"
    BusID          "PCI:0:5:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection

---

### Post by finferflu on 2008-03-24
Try setting synaptics as "SendCoreEvents" and see if that works.
Also, you need to add 
```
Load "synaptics" 
``` in the Module section.

---

### Post by ubrox on 2008-03-24
cool! "SendCoreEvents" diod the trick. However, I did not have to use "Load".

thank you!

---

### Post by finferflu on 2008-03-24
Always happy to help :)

---

