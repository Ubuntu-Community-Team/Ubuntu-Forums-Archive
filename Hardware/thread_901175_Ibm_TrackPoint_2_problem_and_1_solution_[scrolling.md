---
title: "Ibm TrackPoint 2 problem and 1 solution [scrolling]"
date: 2008-08-26
forum: Hardware
---

### Post by sam1948 on 2008-08-26
> Section "InputDevice"
       Identifier  "UltraNav TrackPoint"
       Driver      "mouse"
       Option      "Device"	         "/dev/input/mouse1"
       Option      "Protocol"            "ExplorerPS/2"
       Option      "Emulate3Buttons"     "on"
       Option      "Emulate3TimeOut"     "50"
       Option      "EmulateWheel"        "on"
       Option      "EmulateWheelTimeOut" "200"
       Option      "EmulateWheelButton"  "2"
       Option      "YAxisMapping"        "4 5"
       Option      "XAxisMapping"        "6 7"
       Option      "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier "Mouse2"
    Driver "mouse"
    Option "Protocol" "IMPS/2"
    Option "Device" "/dev/input/mouse2"
    Option "ZAxisMapping" "4 5"
    Option "Buttons" "7"
EndSection

Section "InputDevice"
    Identifier "Mouse0"
    Driver "mouse"
    Option "Protocol" "IMPS/2"
    Option "Device" "/dev/input/mouse2"
    Option "ZAxisMapping" "4 5"
    Option "Buttons" "7"
EndSection


this is the definitions as they works for me in the **/etc/X11/xorg.conf** file

_problem 1_: this worked after a lot of digging on the net so I'm not sure if  u have to install additional software , sorry.
howerver this is the [link to the original post in other place]("http://gentoo-wiki.com/HARDWARE_IBM_Specific_Laptop_Guide#TrackPoint") 

_problem 2_: when attaching a usb mouse the xserver must be restarted in order to recognize that mouse

_problem 3_: when browsing with firefox, navigating backward with the backward button and then trying to scroll the firefox navigates forward

---

### Post by chrisdeckard on 2008-08-26
Here's my relevant sections from xorg.conf:

```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```

It's been a few years since I really messed with X config files, but if I recall, you need to have a generic CorePointer mouse configured for your USB mouse to "just work" when it's plugged in.  If you define it like you are, with /dev/input/mouse2, it's not going to detect it except with X starts up.  At that point it's not really a hot swappable device.  X tries to find it, fails, and ignores it for the future.

Try adding the Configured Mouse section above to your xorg.conf, and try it again.  You'll have to restart X for the changes to take affect.  USB mouse hot swapping works just fine for me, including scroll wheel action.

-Chris

---

### Post by sam1948 on 2008-08-26
Chris thanks a lot for the replay 

about the usb mouse thanks i'll try that,
and about the scrolling problem, it happens with the TrackPoint mouse 
the ibm red joystick in the ThinkPad laptops 
if u have any idea i'lld love to give it a try

---

### Post by bismark on 2008-08-26
Problem 3:

Check out thinkwiki.org for how to configure the TrackPoint, it has specific info for the Firefox problem of going backwards when you don't want to.
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Problem 2:

Reconfigure your TrackPoint stanza in xorg.conf to contain the CorePointer option.  Here's mine as example.
```

Section "InputDevice"
        Identifier      "TrackPoint"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "on"
        Option          "Emulate3TimeOut"       "50"
        Option          "EmulateWheel"          "on"
        Option          "EmulateWheelTimeOut"   "200"
        Option          "EmulateWheelButton"    "2"
        Option          "YAxisMapping"          "4 5"
        Option          "XAxisMapping"          "6 7"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "UsbMouse"
        Driver          "mouse"
EndSection

<snip>

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "TrackPoint"
EndSection

```

---

### Post by chrisdeckard on 2008-08-26
I don't have my Track Point setup that way, so I don't know how to help you.  I do have the pad setup to do scrolling, and that works just fine.

-Chris

---

### Post by bismark on 2008-08-26
> **sam1948 said:**
> Chris thanks a lot for the replay 

about the usb mouse thanks i'll try that,
and about the scrolling problem, it happens with the TrackPoint mouse 
the ibm red joystick in the ThinkPad laptops 
if u have any idea i'lld love to give it a try

[URL="http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Configure_firefox_for_using_trackpoint_horizontal_scrolling"]How to configure horizontal scrolling & back\forward in Firefox
[/URL]

---

### Post by sam1948 on 2008-08-26
thanks a lot to u all
worked perfect

---

### Post by DomesDKG on 2010-03-10
I'm having trouble getting the scrolling feature to work on my T400.  I tried the x server method described on [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint), but it still doesn't work.  Here's the contents of my /etc/X11/xorg.conf file:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

Section "InputDevice"
       Identifier "TPPS/2 IBM TrackPoint"
       Driver     "evdev"
       Option     "Device" "/dev/input/by-path/platform-i8042-serio-2-event-mouse"
       Option     "GrabDevice" "False"
       Option     "EmulateWheel" "true" #Enable wheel emulation for the Trackpoint
       Option     "EmulateWheelButton" "2" #Use the middle button for the emulation
       Option     "XAxisMapping" "6 7" #Map trackpoint X axis to X axis of emulated wheel
       Option     "YAxisMapping" "4 5" #Map trackpoint Y axis to Y axis of emulated wheel
EndSection

any ideas what I'm doing wrong?

---

