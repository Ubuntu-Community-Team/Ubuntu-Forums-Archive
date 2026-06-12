---
title: "help with touchpad netbook averatec"
date: 2009-05-17
forum: Hardware
---

### Post by thepianist on 2009-05-17
HI

I installed ubuntu 9.04 in a averatec netbook with intel atom , I amhaving some problems and one of them is with touchpad

My xinput list shows:

 "Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"SynapticsTouchpad"    id=2    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"AT Translated Set 2 keyboard"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=4    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=5    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"Genius NetScroll + Traveler"    id=6    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

I installed tpconfig and it shows

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).


I tried to work with xorg.conf using some information about synaptics, and here is my xorg.conf

Section "InputDevice"
   Identifier  "SynapticsTouchpad"
   Driver      "synaptics"
   Option      "AlwaysCore"        "true"  # send events to CorePointer
  #Option      "Device"            "/dev/input/mice"
   Option      "Device"            "/dev/psaux"
   Option      "Protocol"          "auto-dev"
   Option      "SHMConfig"         "false" # configurable at runtime? security risk
   Option      "LeftEdge"          "1700"  # x coord left
   Option      "RightEdge"         "5300"  # x coord right
   Option      "TopEdge"           "1700"  # y coord top
   Option      "BottomEdge"        "4200"  # y coord bottom
   Option      "FingerLow"         "25"    # pressure below this level triggers release
   Option      "FingerHigh"        "30"    # pressure above this level triggers touch
   Option      "MaxTapTime"        "180"   # max time in ms for detecting tap
   Option      "VertEdgeScroll"    "true"  # enable vertical scroll zone
   Option      "HorizEdgeScroll"   "true"  # enable horizontal scroll zone
   Option      "CornerCoasting"    "true"  # enable continuous scroll with finger in corner
   Option      "CoastingSpeed"     "0.30"  # corner coasting speed
   Option      "VertScrollDelta"   "100"   # edge-to-edge scroll distance of the vertical scroll
   Option      "HorizScrollDelta"  "100"   # edge-to-edge scroll distance of the horizontal scroll
   Option      "MinSpeed"          "0.10"  # speed factor for low pointer movement
   Option      "MaxSpeed"          "0.60"  # maximum speed factor for fast pointer movement
   Option      "AccelFactor"       "0.0020"    # acceleration factor for normal pointer movements
   Option      "VertTwoFingerScroll"   "true"    # vertical scroll anywhere with two fingers
   Option      "HorizTwoFingerScroll"  "true"    # horizontal scroll anywhere with two fingers
   Option      "TapButton1" "1"
   Option      "TapButton2" "2"
   Option      "TapButton3" "3"
EndSection


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
#    InputDevice "USB Mouse" "CorePointer"
    InputDevice "SynapticsTouchPad" "SendCoreEvents"
EndSection

Section "Module"
    Load "freetype"
    Load "synaptics"
    Load "evdev"
EndSection

but in my /var/log/Xorg.0.log
......
(II) intel(0): Setting screen physical size to 270 x 158
(II) Synaptics touchpad driver version 0.99.3
SynapticsTouchpad no synaptics event device found
......

and it doesn't work

can anybody helps me ? thanks a lot !

---

### Post by thepianist on 2009-05-22
Hi

I solved my problem following this :

[http://agoranetbook.kayno.net/2009/04/25/oh-my-touchpad-doesnt-work/](http://agoranetbook.kayno.net/2009/04/25/oh-my-touchpad-doesnt-work/)

now when I run:

dmesg | grep input 

I have  input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9

I hope that this can help others with same problem

hugs

---

