---
title: "touchpad issues on macbook"
date: 2011-01-12
forum: Hardware
---

### Post by emkersyt on 2011-01-12
Hi everybody!
I recently installed Ubuntu 10.10 on my MacBook 5.2.
The touchpad is too sensitive which renders it kind of unusable and seems to be a common problem on MacBooks/Ubuntu.
First of all all configured /etc/X11/xorg.conf in the following way:

```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "synaptics"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "SendCoreEvents" "true"
    Option         "LeftEdge" "100"
    Option         "RightEdge" "1120"
    Option         "TopEdge" "50"
    Option         "BottomEdge" "310"
    Option         "FingerLow" "5"
    Option         "FingerHigh" "120"
    Option         "MaxTapTime" "100"
    Option         "MaxTapMove" "170"
    Option         "MaxDoubleTapTime" "180"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "50"
    Option         "MinSpeed" "0.49"
    Option         "MaxSpeed" "0.90"
    Option         "AccelFactor" "0.0010"
    Option         "LockedDrags" "false"
    Option         "TapButton1" "1"
    Option         "TapButton2" "3"
    Option         "TapButton3" "2"
    Option         "VertTwoFingerScroll" "true"
    Option         "HorizTwoFingerScroll" "false"
    Option         "FastTaps" "true"
    Option         "VertEdgeScroll" "false"
    Option         "HorizEdgeScroll" "false"
    Option         "SHMConfig" "on"
EndSection


```
These settings seem to be ignored as the output from synclient shows:

```

Parameter settings:
    LeftEdge                = 103
    RightEdge               = 1112
    TopEdge                 = 48
    BottomEdge              = 527
    FingerLow               = 29
    FingerHigh              = 35
    FingerPress             = 300
    MaxTapTime              = 180
    MaxTapMove              = 59
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 330
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 26
    HorizScrollDelta        = 26
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 1
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.0372024
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 35
    EdgeMotionMaxZ          = 187
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 107
    EdgeMotionUseAlways     = 0
    UpDownScrolling         = 1
    LeftRightScrolling      = 1
    UpDownScrollRepeat      = 1
    LeftRightScrollRepeat   = 1
    ScrollButtonRepeat      = 100
    TouchpadOff             = 0
    GuestMouseOff           = 0
    LockedDrags             = 0
    LockedDragTimeout       = 5000
    RTCornerButton          = 2
    RBCornerButton          = 3
    LTCornerButton          = 0
    LBCornerButton          = 0
    TapButton1              = 1
    TapButton2              = 3
    TapButton3              = 2
    ClickFinger1            = 1
    ClickFinger2            = 3
    ClickFinger3            = 2
    CircularScrolling       = 0
    CircScrollDelta         = 0.1
    CircScrollTrigger       = 0
    CircularPad             = 0
    PalmDetect              = 0
    PalmMinWidth            = 10
    PalmMinZ                = 234
    CoastingSpeed           = 0
    PressureMotionMinZ      = 35
    PressureMotionMaxZ      = 187
    PressureMotionMinFactor = 1
    PressureMotionMaxFactor = 1
    GrabEventDevice         = 1
    TapAndDragGesture       = 1
    AreaLeftEdge            = 0
    AreaRightEdge           = 0
    AreaTopEdge             = 0
    AreaBottomEdge          = 0
    JumpyCursorThreshold    = 0

```

Trying to change the driver for the [_**multi touch X driver**_]("http://bitmath.org/code/multitouch/") failed because my xorg.conf won't take any *Section "Input Class"*. The vim colors show an error there and the whole xorg.conf won't be accepted by X.

I can use synclient to change the behaviour of the touchpad so it doesn't get too much in the way. Trouble is I can't find a way to make it permanant. After restart all settings are resetted. 
[**_Here_**]("http://en.gentoo-wiki.com/wiki/Synaptics_Touchpad/Xorg_7.3") I found the information that this has to be done with HAL and I tried that but it didn't work. 
First of all I've got some confusion about where HAL keeps it's settings: in /etc/fdi/hal/policy/... or in /usr/share/hal/fdi/policy/...

Anyway, just when I was about to try to make the HAL policies work I found a couple of hints on the net saying that HAL was deprecated and that one should use udev instead of it.

So the next step was that I followed these [_**instructions**_]("http://matija.suklje.name/?q=node/213") to replace HAL with udev but to no avail. X-server doesn't start up anymore until I get rid of the newly created xorg.con.d directory and replace it with a the former xorg.conf.

Before I started fiddling around with all that I installed the x-server-dev following someones advice.

If someone could point out the way where to start solving this or what finally is the state of the art of xorg.conf and HAL vs. udev I'd really appreciate your help.

---

### Post by pi/roman on 2011-01-12
The "inputdevice" identifier requires a reference in "serverlayout" like:

```
Section "ServerLayout"
          Identifier    "X.org Configured"
          Screen      "Default Screen"
          InputDevice "Mouse0"
EndSection
```

---

### Post by emkersyt on 2011-01-13
My xorg.conf looks like this now:

```

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

#Section "InputDevice"
#    Identifier     "Mouse0"
#    Driver         "synaptics"
#    Option         "Protocol" "auto-dev"
#    Option         "Device" "/dev/psaux"
#    Option         "SendCoreEvents" "true"
#    Option         "LeftEdge" "100"
#    Option         "RightEdge" "1120"
#    Option         "TopEdge" "50"
#    Option         "BottomEdge" "310"
#    Option         "FingerLow" "5"
#    Option         "FingerHigh" "120"
#    Option         "MaxTapTime" "100"
#    Option         "MaxTapMove" "170"
#    Option         "MaxDoubleTapTime" "180"
#    Option         "VertScrollDelta" "20"
#    Option         "HorizScrollDelta" "50"
#    Option         "MinSpeed" "0.49"
#    Option         "MaxSpeed" "0.90"
#    Option         "AccelFactor" "0.0010"
#    Option         "LockedDrags" "false"
#    Option         "TapButton1" "1"
#    Option         "TapButton2" "3"
#    Option         "TapButton3" "2"
#    Option         "VertTwoFingerScroll" "true"
#    Option         "HorizTwoFingerScroll" "false"
#    Option         "FastTaps" "true"
#    Option         "VertEdgeScroll" "false"
#    Option         "HorizEdgeScroll" "false"
#    Option         "SHMConfig" "on"
#EndSection

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
EndSection

Section "ServerLayout"
          Identifier    "X.org Configured"
          Screen      "Default Screen"
#         InputDevice "Mouse0"
	  InputClass "Multitouch Touchpad"
EndSection

```

I commented the synaptics section out to try the multitouch driver.
However, the problem remains that that file can't be parsed by the server. Here is the relevant piece of log:

```


[    21.276] (==) Using config file: "/etc/X11/xorg.conf"
[    21.276] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.288] Parse error on line 52 of section ServerLayout in file /etc/X11/xorg.conf
	"InputClass" is not a valid keyword in this section.
[    21.288] (EE) Problem parsing the config file
[    21.288] (EE) Error parsing the config file
[    21.288] 


```

For me it looks like my xorg.conf doesn´t know how to handle "InputClass" for whatever reason.

---

### Post by pi/roman on 2011-01-13
The "InputClass" identifier is applied to an entire class of devices which in this case would be all of the touchpads on your system and should not be listed in "ServerLayout".  The identifier for "InputDevice" references only a single device on your system and it should be listed in your "ServerLayout" section. You can uncomment the respective lines and it will be applied to your touchpad along with the "InputClass" settings. Alternatively, since you probably only have 1 touchpad on your system anyway, you could add all of your device settings to your "InputClass" section. So it would look like this:
```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

Section "InputClass"
    MatchIsTouchpad "true"
    Identifier "Multitouch Touchpad"
    Driver "multitouch"
    Option         "Protocol" "auto-dev"
    Option         "Device" "/dev/psaux"
    Option         "SendCoreEvents" "true"
    Option         "LeftEdge" "100"
    Option         "RightEdge" "1120"
    Option         "TopEdge" "50"
    Option         "BottomEdge" "310"
    Option         "FingerLow" "5"
    Option         "FingerHigh" "120"
    Option         "MaxTapTime" "100"
    Option         "MaxTapMove" "170"
    Option         "MaxDoubleTapTime" "180"
    Option         "VertScrollDelta" "20"
    Option         "HorizScrollDelta" "50"
    Option         "MinSpeed" "0.49"
    Option         "MaxSpeed" "0.90"
    Option         "AccelFactor" "0.0010"
    Option         "LockedDrags" "false"
    Option         "TapButton1" "1"
    Option         "TapButton2" "3"
    Option         "TapButton3" "2"
    Option         "VertTwoFingerScroll" "true"
    Option         "HorizTwoFingerScroll" "false"
    Option         "FastTaps" "true"
    Option         "VertEdgeScroll" "false"
    Option         "HorizEdgeScroll" "false"
    Option         "SHMConfig" "on"
EndSection
```

---

### Post by emkersyt on 2011-01-13
Hi pi/roman! With your version of xorg.conf the X-server loads and the graphical environment shows up. Still, the "InputClass" section is not recognized. The vim colours show that something is wrong (the Endsection tag is highlighted red and also the Section tag is white - should be yellow). Consequently after starting X the touchpad is not recognized.
I think your xorg.conf is correct. I guess I need to know why my X doesn't support the "InputClass" tag.

This is the Xserver version:
```

arytloc@sarytash:~$ Xorg -version

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux sarytash 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=e395a091-e108-4c78-8f42-1a2f687019af ro acpi=off
Build Date: 09 January 2011  12:14:58PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.

```

---

### Post by pi/roman on 2011-01-14
I don't think I would jump to the conclusion that InputClass doesn't work unless you have more evidence of it. The Vim highlighting is normal and has no effect on the boot process. The touchpad might not be configured properly for other reasons. You should look through Xorg.0.log to see if you can identify the issue. It could be a conflict with the "InputClass" configurations in /usr/share/X11/xorg.conf.d.

---

### Post by emkersyt on 2011-01-15
Thanks pi/roman! After doing several test (and dozens of restarting X) I think I'm getting pretty close: 
The /etc/X11/xorg.conf on Maverick Meerkat doesn't seem to work for much more than the display settings.
All input device related stuff is edited in several files in the /usr/share/X11/xorg.conf.d/ directory. In these the "InputClass" tag is recognized.
Creating the xorg.conf.d directory under /etc/X11/ didn't work for me.

Finally the multitouch driver got loaded but subsequently unloaded again.
The /var/log/Xorg.0.log reads: 

```

[  1867.420] (II) config/udev: Adding input device appletouch (/dev/input/event3)
[  1867.420] (**) appletouch: Applying InputClass "Multitouch Touchpad"
[  1867.420] (II) LoadModule: "multitouch"
[  1867.420] (II) Loading /usr/lib/xorg/modules/input/multitouch.so
[  1867.420] (II) Module multitouch: vendor="X.Org Foundation"
[  1867.420] 	compiled for 1.9.0, module version = 0.1.0
[  1867.420] 	Module class: X.Org XInput Driver
[  1867.420] 	ABI class: X.Org XInput driver, version 11.0
[  1867.420] (**) appletouch: always reports core events
[  1867.420] (II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
[  1867.420] (II) device control: init
[  1867.420] (**) Option "Device" "/dev/input/event3"
[  1867.420] (II) multitouch: devname: appletouch
[  1867.420] (II) multitouch: devid: 5ac 22a 9
[  1867.420] (II) multitouch: caps: left
[  1867.420] (II) pointer_control
[  1867.420] (**) appletouch: (accel) keeping acceleration scheme 1
[  1867.420] (**) appletouch: (accel) acceleration profile 0
[  1867.420] (**) appletouch: (accel) acceleration factor: 2.000
[  1867.420] (**) appletouch: (accel) acceleration threshold: 4
[  1867.420] (II) device control: on
[  1867.420] (II) pointer_property
[  1867.420] (II) pointer_property
[  1867.420] (II) config/udev: Adding input device appletouch (/dev/input/mouse1)
[  1867.420] (**) appletouch: Applying InputClass "Multitouch Touchpad"
[  1867.420] (**) appletouch: always reports core events
[  1867.420] (II) XINPUT: Adding extended input device "appletouch" (type: TOUCHPAD)
[  1867.420] (II) device control: init
[  1867.420] (**) Option "Device" "/dev/input/mouse1"
[  1867.420] (EE) multitouch: cannot configure device
[  1867.420] (EE) Couldn't init device "appletouch"
[  1867.420] (II) UnloadModule: "multitouch"

```

If I'm right now the multitouch driver is making trouble. The synaptics driver does load the "appletouch" module flawlessly. I installed the multitouch driver from the the mactel ppa via apt-get.
Any ideas?

---

### Post by pi/roman on 2011-01-19
I'm sorry, i dont; use macs. It's not that i wouldn't like to have one, but i just don't. From the log it appears as though the multitouch driver is having trouble communicating with your device:
> [  1867.420] (EE) multitouch: cannot configure device
[  1867.420] (EE) Couldn't init device "appletouch"You said before that synpatics driver worked ok but you needed to figure out how  to save the configuration. That may be the way to go if multitouch doesn't work.

---

