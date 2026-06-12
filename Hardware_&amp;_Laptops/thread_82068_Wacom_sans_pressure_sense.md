---
title: "Wacom sans pressure sense"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by dustyub on 2005-10-25
I've read several tutorials in these forums for tablet pressure functionality. I can't seem to make it work correctly though. 

I have a Wacom USB Graphire 3 tablet. I have no other mice style input devices plugged in. 

The exact problem is: 
When Gimp loads, I create a new file, I've set the input device settings previously, to 'stylus,' 'cursor,' and 'eraser.' They are all set from 'disable' to 'screen.' I start to paint, and the pressure sensitivity works, however when I lift the stylus up it doesn't recognize that I have lifted it. Instead the program continues to act as though the stylus is touching the tablet even when I am using the Wacom's mouse. The result is that I am unable to use my mouse/tablet again until I 'crtl + alt + backspace.' Additionally the eraser doesn't work when I flip over the pen. 

My xorg.conf (relating to input devices) is as follows: 
```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mouse0"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "5 4"
EndSection

Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Mode" "relative"
    Option "Type" "cursor"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "stylus"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection
``` 
I also added the input device references(?) to the bottom part: 
```
Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection
``` 
Anyway, if you have a suggestion, I'd be happy to hear it, thank you in advance.

---

### Post by 23meg on 2005-10-25
I'll paste the relevant portions of my working xorg.conf where I have many extra options compared to yours; try adding them one by one and chances are your problem will be solved. This is for a tablet pc digitizer, so don't add the "Device" and "ForceDevice" options. I particularly suspect it has something to do with "InputFashion" and "SendCoreEvents".

```
Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"        "/dev/ttyS0"
    Option        "InputFashion" "Tablet"
    Option        "ForceDevice"    "ISDV4"
    Option        "Name" "GRAPHIRE / INTUOS (SERIAL)"
    Option        "SendCoreEvents" "on"
    Option        "Type"          "cursor"
    Option        "Mode"          "absolute" 
    Option        "Vendor" "WACOM"
    Option        "Speed"         "3.0"
    Option        "Threshold"     "1"
    Option        "Tilt"          "on"
    Option	     "Button2"	"3"
    #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"        "/dev/ttyS0"
    Option        "Type"          "stylus"
    Option        "InputFashion" "Pen"
    Option        "SendCoreEvents" "on"
    Option        "Name"          "GRAPHIRE / INTUOS Stylus (SERIAL)"
    Option        "ForceDevice"    "ISDV4"
    Option        "Mode"          "absolute"
    Option        "Vendor" "WACOM"
    Option        "Tilt"          "on"
    Option        "TiltInvert"    "on"
    Option        "Threshold"     "1"
    Option	     "Button2"	"3"
   #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
 Driver       "wacom"
 Identifier   "eraser"
 Option       "Device" "/dev/ttyS0"
 Option       "InputFashion" "Eraser"
 Option       "Name" "GRAPHIRE / INTUOS Eraser (SERIAL)"
 Option       "Type" "eraser"
 Option       "Mode" "absolute"
 Option       "Vendor" "WACOM"
 Option       "ForceDevice" "ISDV4" 
 Option        "SendCoreEvents" "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Alps Glidepoint" "CorePointer"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection


```

---

### Post by dustyub on 2005-10-25
I've tried all of the various options you supplied and I was unable to get it working. It still maintains the same bizarre and useless behavior.

Thank you for your time and suggestion though, I appreciate the help.

---

