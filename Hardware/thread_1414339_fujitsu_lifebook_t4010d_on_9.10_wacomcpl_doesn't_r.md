---
title: "fujitsu lifebook t4010d on 9.10 wacomcpl doesn't recognize touchscreen?"
date: 2010-02-23
forum: Hardware
---

### Post by djrakun on 2010-02-23
hi all,

I've been messing with my t4010d trying to turn it into a mp3 dj station for a while now. I've bounced around between 64studio, pure:dyne, and now I'm back to ubuntu studio.  The goal is to get an audio optimized kernel with a working touchscreen

I had the touchscreen working on pre-intrepid releases of ubuntu by editing the xorg.conf file, but was tempted to upgrade to ubuntu studio when I read about the wacomcpl.  The wacom control panel does not recognize a device to configure however.

I have wacom-tools and xserver-xorg-input-wacom installed.  I believe one of these was installed by default but i used apt-get to install the other (sorry dont remember which, but i believe that info is moot anyway)

Does anybody have any familiarity with Fujitsu Lifebooks who could possibly lend a hand?  I didn't see any Karmic or Jaunty hardware testing completed in the ubuntu testing repository

---

### Post by Favux on 2010-02-23
Hi djrakun,

Most likely wacom-tools.

You can see why wacomcpl isn't working by entering:
```
xinput -list
```
and see what it is calling your tablet.  If:
```
xsetwacom list
```
is blank, that's why wacomcpl isnt working.

You could try one of the two modified .fdi's attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Read "Jaunty (9.04) & Karmic (9.10) Users" near the top.  Instructions for installing the .fdi's are in Section 2 b).  Instructions for setting up wacomcpl in Section 3.

---

### Post by djrakun on 2010-02-24
thanks for your help.  i followed your instructions and after the reboot it was working!  I got a little too excited and opened up mixxx to play with the pen control and the OS locked up, before i could set anything in wacomcpl.  I did a hard reboot and i lost pen control.  followed the instructions several times after that and pen control was never regained.  

Trying to get back there now.  will let you know if i manage it

---

### Post by B1ler on 2010-03-23
Hi there,

I have the same problem, unfortunately (same laptop too)...

I have replaced the fdi with one of the custom ones that you supply in the long thread. I'm using the      Favux_serial-tablet&tablet-pc_test2_10-wacom.fdi.txt. After restarting it still doesn't show up anything in the wacomcpl...

The devices is listed in xinit -list
```
xinit list
X: user not authorized to run the X server, aborting.
xinit:  Server error.
blerim@blerim-laptop:~$ xinput list
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
"Power Button"    id=2    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Fujitsu FUJ02B1"    id=3    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=4    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Power Button"    id=5    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Translated Set 2 keyboard"    id=6    [XExtensionKeyboard]
    Type is KEYBOARD
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"PnP Device (FUJ02e5)"    id=7    [XExtensionKeyboard]
    Type is Wacom Stylus
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"PnP Device (FUJ02e5) eraser"    id=8    [XExtensionKeyboard]
    Type is Wacom Eraser
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
    Num_buttons is 32
    Num_axes is 6
    Mode is Absolute
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 24576
        Resolution is 2540
    Axis 1 :
        Min_value is 0
        Max_value is 18432
        Resolution is 2540
    Axis 2 :
        Min_value is 0
        Max_value is 255
        Resolution is 1
    Axis 3 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 4 :
        Min_value is -64
        Max_value is 63
        Resolution is 1
    Axis 5 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
"Macintosh mouse button emulation"    id=9    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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
"AlpsPS/2 ALPS GlidePoint"    id=10    [XExtensionPointer]
    Type is TOUCHPAD
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 767
        Resolution is 1
"PS/2 Mouse"    id=11    [XExtensionPointer]
    Type is MOUSE
    Num_buttons is 5
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

```xsetwacom doesn't return anything :(...

Your help is much appreciated!

B1ler

---

### Post by Thomas Kalka on 2010-04-03
I got the stylus working with following xorg.conf:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Module"
	Load "wacom"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/ttyS0"
        Option          "USB"           "off"
        Option          "ForceDevice"   "ISDV4"
        Option          "Type"          "cursor"
        Option          "Mode"          "absolute"
        Option          "Speed"         "3.0"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
#       Option          "MaxX"          "24576"
#       Option          "MaxY"          "18432"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/ttyS0"
        Option          "Type"          "stylus"
        Option          "Mode"          "absolute"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/ttyS0"
        Option          "Type"          "eraser"
        Option          "Mode"          "absolute"
#       Option          "Tilt"          "on"
#       Option          "TiltInvert"    "on"
        Option          "Threshold"     "2"
#       Option          "DebugLevel"    "10"
EndSection

Section "ServerLayout"
        Identifier      "Layout"
        Screen          "Default Screen"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection
```

Additionally I had to symlink 
```
ln -s /dev/event10 /dev/input/event10
```
after upgrading from xubuntu 8.10 to 9.04 to get the touchpad working.

---

