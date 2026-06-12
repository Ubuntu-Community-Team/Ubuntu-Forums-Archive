---
title: "No Synaptics Touchpad"
date: 2010-08-25
forum: Hardware
---

### Post by Droopy_Snowmen on 2010-08-25
I just installed Ubuntu 10.04 and my touchpad does not work AT ALL. No clicks, no mouse motion. Nothing. I've spent a considerable amount of time already trying to fix this, so I thought I would put up a thread. I'm not sure what other information you need, so I'll just start with the basics:

My Computer:
Toshiba Satellite L505-LS5014
Ubuntu 10.04

---

### Post by Droopy_Snowmen on 2010-08-26
I could really use some assistance...

---

### Post by rooster85 on 2010-09-19
> **Droopy_Snowmen said:**
> I could really use some assistance...


having the same issue, am a noob to ubuntu, any help with this would be great

---

### Post by Ayuthia on 2010-09-19
Welcome!  It might be easiest to start with going into a Terminal and posting the results of:
```

lspci -nn
xinput --list

```
That will help us see what the system is currently recognizing.  If you can also attach the /var/log/Xorg.0.log file, that would also help in checking to see what happened when the system was installing the drivers for the devices.

---

### Post by aa-hcl on 2010-09-20
> **Ayuthia said:**
> Welcome!  It might be easiest to start with going into a Terminal and posting the results of:
```

lspci -nn
xinput --list

```That will help us see what the system is currently recognizing.  If you can also attach the /var/log/Xorg.0.log file, that would also help in checking to see what happened when the system was installing the drivers for the devices.


I have also a problem with touchpad (Dell E5510 laptop, ubuntu 10.04), however in my case I can use the touchpad but there are no control tab to tune its performance in the Mouse preference (I want to tune the touchpad since it is too sensitive at the moment and it is activated if my finger is close to it, so I can not enter text comfortably) 

the output for xinput --list:

```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]

```

the output for  lspci -nn:
[code]
aa@aa-i3:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 6000 Series [8086:422c] (rev 35)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 03)
03:00.4 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 03)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
[\code]

---

### Post by Ayuthia on 2010-09-20
> **aa-hcl said:**
> I have also a problem with touchpad (Dell E5510 laptop, ubuntu 10.04), however in my case I can use the touchpad but there are no control tab to tune its performance in the Mouse preference (I want to tune the touchpad since it is too sensitive at the moment and it is activated if my finger is close to it, so I can not enter text comfortably) 

the output for xinput --list:

```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]

```

the output for  lspci -nn:
```

aa@aa-i3:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 6000 Series [8086:422c] (rev 35)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 03)
03:00.4 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 03)
0b:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761e Gigabit Ethernet PCIe [14e4:1680] (rev 10)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
[\code]

Can you also post the results of:
[code]
xinput list-props 12
xinput list-props 14

```
They will help us see the properties of the mouse devices.

---

### Post by aa-hcl on 2010-09-20
> **Ayuthia said:**
> Can you also post the results of:
```

xinput list-props 12
xinput list-props 14

```They will help us see the properties of the mouse devices.

Hi,

Many thanks for your prompt reply!

here is the result:

```

aa@aa-i3:~$ xinput list-props 12
Device 'Macintosh mouse button emulation':
    Device Enabled (118):    1
    Device Accel Profile (238):    0
    Device Accel Constant Deceleration (239):    1.000000
    Device Accel Adaptive Deceleration (241):    1.000000
    Device Accel Velocity Scaling (242):    10.000000
    Evdev Reopen Attempts (236):    10
    Evdev Axis Inversion (243):    0, 0
    Evdev Axes Swap (245):    0
    Axis Labels (246):    "Rel X" (126), "Rel Y" (127)
    Button Labels (247):    "Button Left" (119), "Button Middle" (120), "Button Right" (121), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Middle Button Emulation (248):    2
    Evdev Middle Button Timeout (249):    50
    Evdev Wheel Emulation (250):    0
    Evdev Wheel Emulation Axes (251):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (252):    10
    Evdev Wheel Emulation Timeout (253):    200
    Evdev Wheel Emulation Button (254):    4
    Evdev Drag Lock Buttons (255):    0

```

and for the second one:

```

aa@aa-i3:~$ xinput list-props 14
Device 'PS/2 Generic Mouse':
    Device Enabled (118):    1
    Device Accel Profile (238):    0
    Device Accel Constant Deceleration (239):    1.000000
    Device Accel Adaptive Deceleration (241):    1.000000
    Device Accel Velocity Scaling (242):    10.000000
    Evdev Reopen Attempts (236):    10
    Evdev Axis Inversion (243):    0, 0
    Evdev Axes Swap (245):    0
    Axis Labels (246):    "Rel X" (126), "Rel Y" (127)
    Button Labels (247):    "Button Left" (119), "Button Middle" (120), "Button Right" (121), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Middle Button Emulation (248):    2
    Evdev Middle Button Timeout (249):    50
    Evdev Wheel Emulation (250):    0
    Evdev Wheel Emulation Axes (251):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (252):    10
    Evdev Wheel Emulation Timeout (253):    200
    Evdev Wheel Emulation Button (254):    4
    Evdev Drag Lock Buttons (255):    0

```

---

### Post by Ayuthia on 2010-09-20
You might try this [link]("http://forum.notebookreview.com/6638913-post140.html").  It looks like they were able to get it set up to run with synaptics instead of the evdev driver that yours is currently attached to.

Once you get this file created, you will need to restart X or restart the computer and it should switch over to the synaptics driver.  From there, you should have some options to adjust the sensitivity.  If you are not sure how, please post the results of the xinput list-props for the touchpad again.

If it does not work, please post the /var/log/Xorg.0.log file and we can see what happened.

---

### Post by aa-hcl on 2010-09-20
> **Ayuthia said:**
> You might try this [link]("http://forum.notebookreview.com/6638913-post140.html").  It looks like they were able to get it set up to run with synaptics instead of the evdev driver that yours is currently attached to.

Once you get this file created, you will need to restart X or restart the computer and it should switch over to the synaptics driver.  From there, you should have some options to adjust the sensitivity.  If you are not sure how, please post the results of the xinput list-props for the touchpad again.

If it does not work, please post the /var/log/Xorg.0.log file and we can see what happened.


Hi,

I have tried the above but it looks like it does not work.  Can you please have a look at the information before and may be you can have further ideas how to fix it?

Many THANKS!

Here is what I have done:

1. according to [http://forum.notebookreview.com/6638913-post140.html](http://forum.notebookreview.com/6638913-post140.html)  I firstly did 
"Enable SHMConfig" by 

```

aa@aa-i3:~$ gksudo gedit /etc/X11/xorg.conf

```


adding this to the above file (it was open as empty)

```

Section "InputClass"
        Identifier "enable synaptics SHMConfig"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "SHMConfig" "on"
EndSection

```

Save and close the file and reboot. 

2.  Update the xorg synaptics.conf file. to do this:

```

aa@aa-i3:~$ cd /usr/lib/X11/xorg.conf.d/
aa@aa-i3:/usr/lib/X11/xorg.conf.d$ sudo gedit 10-synaptics.conf

```

and then inserting the part as according to the link above (see the result below).

I then rebooted the laptop, but there is no result:  there is no option to change the touchpad preferences and according to xinput (see below), it still does not recognise the touchpad properly.

Here are the outputs of the relevant files to demonstrate that i have done what is advised in [http://forum.notebookreview.com/6638913-post140.html](http://forum.notebookreview.com/6638913-post140.html) 

the files:

```

aa@aa-i3:~$ cat /etc/X11/xorg.conf
Section "InputClass"
        Identifier "enable synaptics SHMConfig"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "SHMConfig" "on"
EndSection

```

and the other one:

```

aa@aa-i3:~$ cat /usr/lib/X11/xorg.conf.d/10-synaptics.conf
# Section "InputClass"
#     Identifier "touchpad catchall"
#     MatchIsTouchpad "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "synaptics"
# EndSection

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option         "SHMConfig" "true"
    Option        "LeftEdge"        "1752"    # X coordinate for left edge.
    Option        "RightEdge"        "5192"    # X coordinate for right edge #If set SpecialScrollAreaRight is ignored.
    Option        "TopEdge"        "1620"    # Y coordinate for top edge.
    Option        "BottomEdge"        "4236"    # Y coordinate for bottom edge.
#    Option        "SpecialScrollAreaRight""bool"    # Enable scroll region on the right edge as  scroll wheel region.
    Option        "FingerLow"        "30"    # Finger pressure below this level triggers release.
    Option        "FingerHigh"        "31"    # Finger pressure above this level triggers touch.
    Option        "FingerPress"        "250"    # Finger pressure above this value triggers press.
#...                            # A press is equivalent to putting touchpad in trackstick emulation mode.
    Option        "MaxTapTime"        "200"    # Max time in ms for detecting tap.
    Option        "BMaxTapMove"        "100"    # Max finger movement for detecting a tap.
    Option        "MaxDoubleTapTime"    "100"    # Max time in ms for detecting a double tap.
    Option        "SingleTapTimeout"    "100"    # Timeout after a tap to recognize it as a single tap.
    Option        "ClickTime"        "100"    # Duration of mouse click generated by tapping.
    Option        "FastTaps"        "false"    # Driver reacts faster to a single tap, double clicks caused by slow double tapping.
    Option        "VertScrollDelta"    "1"    # Edge-to-edge scroll distance of the vertical scroll.
    Option        "HorizScrollDelta"    "1"    # Edge-to-edge scroll distance of the horizontal scroll.
    Option        "VertEdgeScroll"    "false"    # Enable vertical scroll zone.
    Option        "HorizEdgeScroll"    "false"    # Enable horizontal scroll zone.
    Option        "CornerCoasting"    "false"    # Enable continuous scroll with finger in corner.
    Option        "CoastingSpeed"        "0"    # Corner coasting speed.
    Option        "VertTwoFingerScroll"    "true"    # Vertical scroll anywhere with two fingers.
    Option        "HorizTwoFingerScroll"    "true"    # Horizontal scroll anywhere with two fingers.
    Option        "MinSpeed"        "0.4"    # Speed factor for low pointer movement.
    Option        "MaxSpeed"        "0.6"    # Max speed factor for fast pointer movement.
    Option        "AccelFactor"        "0.01"    # Acceleration factor for normal pointer movements
    Option        "TrackstickSpeed"    "40"    # Speed  scale in trackstick emulation mode.
    Option        "EdgeMotionMinZ"    "30"    # Finger pressure at which min edge motion speed is set.
    Option        "EdgeMotionMaxZ"    "150"    # Finger pressure at which max edge motion speed is set.
    Option        "EdgeMotionMinSpeed"    "1"    # Slowest setting for edge motion speed.
    Option        "EdgeMotionMaxSpeed"    "400"    # Fastest setting for edge motion speed.
    Option        "EdgeMotionUseAlways"    "false"    # If off, egde motion is used only when dragging. If on, also used for normal movements.
    Option        "PressureMotionMinZ"    "50"    # Finger pressure at which minimum pressure motion factor is applied.
    Option        "PressureMotionMaxZ"    "150"    # Finger pressure at which maximum pressure motion factor is applied.
    Option        "PressureMotionMinFactor""1"    # Lowest setting for pressure motion factor. 
    Option        "PressureMotionMaxFactor""1"    # Greatest setting for pressure motion factor.
     Option        "UpDownScrolling"    "true"    # If on, the up/down buttons generate button 4/5 events. 
#...                            # If off, the up button generates a double click, the down button generates a button 2 event. 
    Option        "LeftRightScrolling"    "false"    # If on, the left/right buttons generate button 6/7  events.   
#...                            # If off, the left/right buttons both generate button 2 events.
    Option        "UpDownScrollRepeat"    "false"    # If on, when the up/down buttons are used for scrolling, will send auto-repeating 4/5 events, 
#...                            # with the delay between repeats determined by ScrollButtonRepeat.
    Option        "LeftRightScrollRepeat"    "false"    # If on, when the left/right buttons are used for scrolling, will send auto-repeating 6/7 events
#...                            # with the delay between repeats determined by ScrollButtonRepeat.
    Option        "ScrollButtonRepeat"    "100"    # Time in msec between repeats of button events  4-7 from the up/down/left/right scroll buttons.
    Option        "EmulateMidButtonTime"    "500"    # Maximum time in ms for middle button emulation.
    Option        "EmulateTwoFingerMinZ"    "60"    # For Alps touchpads, sets Z pressure threshold to emulate a two finger press.
    Option        "EmulateTwoFingerMinW"    "500"    # Some touchpads report a two-finger touch as wide finger. This emulates a two finger press. 
#...                            # This  feature works best with (PalmDetect) off. 
    Option        "TouchpadOff"        "0"    # Switch off the touchpad, enabled = 0 / switched off = 1 / only tapping and scrolling off \ 2.
    Option        "GuestMouseOff"        "0"    # Switch on/off guest mouse. 
    Option        "LockedDrags"        "0"    # If off, a tap and drag gesture ends when you release the finger. 
#...                            # If on, the gesture is active until you tap a second time or until LockedDragTimeout expires.
    Option        "LockedDragTimeout"    "5000"    # How long in ms for the LockedDrags mode to be automatically turned off after finger is released.
    Option        "CircularScrolling"    "false"    # If on, circular scrolling is used.
    Option        "CircScrollDelta"    "30"    # Move angle (radians) of finger to generate a scroll event.
    Option        "CircScrollTrigger"    "0"    # Trigger region on the touchpad to start circular scrolling.
#...                            # All Edges = 0. Top Edge = 1. Top Right Corner = 2. Right Edge = 3. Bottom Right Corner = 4.
#...                            # Bottom Edge = 5. Bottom Left Corner = 6. Left Edge = 7. Top Left Corner = 8.
    Option        "RTCornerButton"    "1"    # Which mouse button is reported on a right top corner tap. Set to 0 to disable.
    Option        "RBCornerButton"    "1"    # Which mouse button is reported on a right bottom corner tap. Set to 0 to disable.
    Option        "LTCornerButton"    "1"    # Which mouse button is reported on a left top corner tap. Set to 0 to disable.
    Option        "LBCornerButton"    "1"    # Which mouse button is reported on a left bottom corner tap. Set to 0 to disable.
    Option        "TapButton1"        "1"
    Option        "TapButton2"        "2"
    Option        "TapButton3"        "3"
    Option        "PalmDetect"        "true"    # If palm detection should be enabled.
    Option        "PalmMinWidth"        "10"    # Minimum finger width at which touch is considered a palm.
     Option        "PalmMinZ"        "200"    # Minimum finger pressure at which touch is considered a palm.
    Option        "GrabEventDevice"    "true"  # If true, no other user space or kernel space program sees the touchpad events. 
#...                            # This is desirable if the X config file includes /dev/input/mice as an input device.
#...                            # This is undesirable if you want to monitor the device from user space. 
    Option        "TapAndDragGesture"    "true" # Switch on/off the tap-and-drag gesture. The gesture is enabled by default.
    Option        "AreaLeftEdge"        "0"    # Ignore movements, scrolling and tapping which take place left of this edge.
    Option        "AreaRightEdge"        "0"    # Ignore movements, scrolling and tapping which take place right of this edge. 
    Option        "AreaTopEdge"        "0"    # Ignore movements, scrolling and tapping which take place above this edge.
    Option        "AreaBottomEdge"    "0"    # Ignore movements, scrolling and tapping which take place below this edge. 
    Option        "JumpyCursorThreshold"    "100"    # Set the threshold above which movement events are ignored on single-touch touchpads. 
#...                            # This option is disabled by default.
EndSection

Section "InputClass"
    Identifier "Dell Inspiron embedded buttons quirks"
    MatchTag "inspiron_1011|inspiron_1012"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection
aa@aa-i3:~$ 

```

the xinput still does not see touchpad properly as before:

```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]

```

and the log:

```

aa@aa-i3:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux aa-i3 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=5886de99-e40d-4a01-b093-18a530938d33 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Sep 20 17:38:12 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0046:1028:0428 Intel Corporation Core Processor Integrated Graphics Controller rev 2, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00008080/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
(--) intel(0): Chipset: "Arrandale"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP3 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output DP1
(II) intel(0): Manufacturer: LGD  Model: 29e  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.4
(II) intel(0): Digital Display Input
(II) intel(0): 6 bits per channel
(II) intel(0): Digital interface is DisplayPort
(II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): Preferred mode is native pixel format and refresh rate
(II) intel(0): redX: 0.617 redY: 0.349   greenX: 0.314 greenY: 0.597
(II) intel(0): blueX: 0.151 blueY: 0.057   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 96.0 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1728 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 64.2 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1740 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 922 v_border: 0
(II) intel(0):  P727R&#65533;156WD1
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0030e49e0200000000
(II) intel(0):     0013010495221378021be59e59509826
(II) intel(0):     0e505400000001010101010101010101
(II) intel(0):     0101010101018025408060841a303020
(II) intel(0):     350058c2100000181419408c60841630
(II) intel(0):     3020350058c210000018000000fe0050
(II) intel(0):     37323752803135365744310a00000000
(II) intel(0):     00004131190000000009010a202000da
(II) intel(0): Printing probed modes for output DP1
(II) intel(0): Modeline "1600x900"x60.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x40.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP3
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output DP1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP3 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output DP1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event8)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
(**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_2M: always reports core events
(**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
(II) Laptop_Integrated_Webcam_2M: Found keys
(II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event6"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event13)
(**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Generic Mouse: always reports core events
(**) PS/2 Generic Mouse: Device: "/dev/input/event13"
(II) PS/2 Generic Mouse: Found 3 mouse buttons
(II) PS/2 Generic Mouse: Found relative axes
(II) PS/2 Generic Mouse: Found x and y relative axes
(II) PS/2 Generic Mouse: Configuring as mouse
(**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
(II) PS/2 Generic Mouse: initialized for relative axes.
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)

```

---

### Post by Ayuthia on 2010-09-20
From your Xorg.0.log, it still looks like the evdev rule is grabbing the device.

You might try to change the /etc/X11/xorg.conf.d/10-synaptics.conf file to have the first few lines look like:
```

Section "InputClass"
    Identifier "touchpad catchall"
#    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event13"
    Driver "synaptics"

```
instead of:
```

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

```
To see if the rule gets picked up.

I am still checking to see if your touchpad is supported by synaptics or not.  I know that some are still using the evdev driver and I have not see if there is a solution for the sensitivity for it or not.

EDIT:
Can you also post the results for the following:
```

dmesg|grep -i alps

```
I would like to see if the device is found during the initial startup.

---

### Post by aa-hcl on 2010-09-21
> **Ayuthia said:**
> From your Xorg.0.log, it still looks like the evdev rule is grabbing the device.

You might try to change the /etc/X11/xorg.conf.d/10-synaptics.conf file to have the first few lines look like:
```

Section "InputClass"
    Identifier "touchpad catchall"
#    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event13"
    Driver "synaptics"

```instead of:
```

Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"

```To see if the rule gets picked up.

I am still checking to see if your touchpad is supported by synaptics or not.  I know that some are still using the evdev driver and I have not see if there is a solution for the sensitivity for it or not.

EDIT:
Can you also post the results for the following:
```

dmesg|grep -i alps

```I would like to see if the device is found during the initial startup.


Hi,

I think there is some confusion where is the file 10-synaptics.conf.

In the link above ( [http://forum.notebookreview.com/6638913-post140.html](http://forum.notebookreview.com/6638913-post140.html) ) this file is in /usr/lib/...  while in your last post you mention it to be in /etc/lib.  For my case there is not such file (and folder!) in /etc/ :

```

aa@aa-i3:~$ cat /etc/X11/xorg.conf.d/10-synaptics.conf
cat: /etc/X11/xorg.conf.d/10-synaptics.conf: No such file or directory
aa@aa-i3:~$ cd /etc/X11/xorg.conf.d/
bash: cd: /etc/X11/xorg.conf.d/: No such file or directory
aa@aa-i3:~$ 

```

But there is the file in /usr/lib:

```

aa@aa-i3:~$ ls -all /usr/lib/X11/xorg.conf.d/10-synaptics.conf
-rw-r--r-- 1 root root 8021 2010-09-20 17:06 /usr/lib/X11/xorg.conf.d/10-synaptics.conf
aa@aa-i3:~$ 

```

May this be the problem?

You also asked to post the results of the following command:
```

aa@aa-i3:~$ dmesg|grep -i alps
aa@aa-i3:~$ dmesg | grep -i alps
aa@aa-i3:~$ 
aa@aa-i3:~$ 

```

you see it does not give any output.... even for the root:

```

root@aa-i3:~# dmesg|grep -i alps
root@aa-i3:~# dmesg | grep -i alps
root@aa-i3:~# 

```

Anyway, let me try to change the setting (i.e. comment out one line) in  /usr/lib/X11/xorg.conf.d/10-synaptics.conf  and I will post the result in several minutes...


Many thanks!!!

---

### Post by aa-hcl on 2010-09-21
I have now tried further steps:


```

root@aa-i3:~# gedit /usr/lib/X11/xorg.conf.d/10-synaptics.conf
root@aa-i3:~# cat /usr/lib/X11/xorg.conf.d/10-synaptics.conf
# Section "InputClass"
#     Identifier "touchpad catchall"
#     MatchIsTouchpad "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "synaptics"
# EndSection

Section "InputClass"
    Identifier "touchpad catchall"
#    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option         "SHMConfig" "true"
    Option        "LeftEdge"        "1752"    # X coordinate for left edge.
    Option        "RightEdge"        "5192"    # X coordinate for right edge #If set SpecialScrollAreaRight is ignored.
    Option        "TopEdge"        "1620"    # Y coordinate for top edge.
    Option        "BottomEdge"        "4236"    # Y coordinate for bottom edge.
#    Option        "SpecialScrollAreaRight""bool"    # Enable scroll region on the right edge as  scroll wheel region.
    Option        "FingerLow"        "30"    # Finger pressure below this level triggers release.
    Option        "FingerHigh"        "31"    # Finger pressure above this level triggers touch.
    Option        "FingerPress"        "250"    # Finger pressure above this value triggers press.
#...                            # A press is equivalent to putting touchpad in trackstick emulation mode.
    Option        "MaxTapTime"        "200"    # Max time in ms for detecting tap.
    Option        "BMaxTapMove"        "100"    # Max finger movement for detecting a tap.
    Option        "MaxDoubleTapTime"    "100"    # Max time in ms for detecting a double tap.
    Option        "SingleTapTimeout"    "100"    # Timeout after a tap to recognize it as a single tap.
    Option        "ClickTime"        "100"    # Duration of mouse click generated by tapping.
    Option        "FastTaps"        "false"    # Driver reacts faster to a single tap, double clicks caused by slow double tapping.
    Option        "VertScrollDelta"    "1"    # Edge-to-edge scroll distance of the vertical scroll.
    Option        "HorizScrollDelta"    "1"    # Edge-to-edge scroll distance of the horizontal scroll.
    Option        "VertEdgeScroll"    "false"    # Enable vertical scroll zone.
    Option        "HorizEdgeScroll"    "false"    # Enable horizontal scroll zone.
    Option        "CornerCoasting"    "false"    # Enable continuous scroll with finger in corner.
    Option        "CoastingSpeed"        "0"    # Corner coasting speed.
    Option        "VertTwoFingerScroll"    "true"    # Vertical scroll anywhere with two fingers.
    Option        "HorizTwoFingerScroll"    "true"    # Horizontal scroll anywhere with two fingers.
    Option        "MinSpeed"        "0.4"    # Speed factor for low pointer movement.
    Option        "MaxSpeed"        "0.6"    # Max speed factor for fast pointer movement.
    Option        "AccelFactor"        "0.01"    # Acceleration factor for normal pointer movements
    Option        "TrackstickSpeed"    "40"    # Speed  scale in trackstick emulation mode.
    Option        "EdgeMotionMinZ"    "30"    # Finger pressure at which min edge motion speed is set.
    Option        "EdgeMotionMaxZ"    "150"    # Finger pressure at which max edge motion speed is set.
    Option        "EdgeMotionMinSpeed"    "1"    # Slowest setting for edge motion speed.
    Option        "EdgeMotionMaxSpeed"    "400"    # Fastest setting for edge motion speed.
    Option        "EdgeMotionUseAlways"    "false"    # If off, egde motion is used only when dragging. If on, also used for normal movements.
    Option        "PressureMotionMinZ"    "50"    # Finger pressure at which minimum pressure motion factor is applied.
    Option        "PressureMotionMaxZ"    "150"    # Finger pressure at which maximum pressure motion factor is applied.
    Option        "PressureMotionMinFactor""1"    # Lowest setting for pressure motion factor. 
    Option        "PressureMotionMaxFactor""1"    # Greatest setting for pressure motion factor.
     Option        "UpDownScrolling"    "true"    # If on, the up/down buttons generate button 4/5 events. 
#...                            # If off, the up button generates a double click, the down button generates a button 2 event. 
    Option        "LeftRightScrolling"    "false"    # If on, the left/right buttons generate button 6/7  events.   
#...                            # If off, the left/right buttons both generate button 2 events.
    Option        "UpDownScrollRepeat"    "false"    # If on, when the up/down buttons are used for scrolling, will send auto-repeating 4/5 events, 
#...                            # with the delay between repeats determined by ScrollButtonRepeat.
    Option        "LeftRightScrollRepeat"    "false"    # If on, when the left/right buttons are used for scrolling, will send auto-repeating 6/7 events
#...                            # with the delay between repeats determined by ScrollButtonRepeat.
    Option        "ScrollButtonRepeat"    "100"    # Time in msec between repeats of button events  4-7 from the up/down/left/right scroll buttons.
    Option        "EmulateMidButtonTime"    "500"    # Maximum time in ms for middle button emulation.
    Option        "EmulateTwoFingerMinZ"    "60"    # For Alps touchpads, sets Z pressure threshold to emulate a two finger press.
    Option        "EmulateTwoFingerMinW"    "500"    # Some touchpads report a two-finger touch as wide finger. This emulates a two finger press. 
#...                            # This  feature works best with (PalmDetect) off. 
    Option        "TouchpadOff"        "0"    # Switch off the touchpad, enabled = 0 / switched off = 1 / only tapping and scrolling off \ 2.
    Option        "GuestMouseOff"        "0"    # Switch on/off guest mouse. 
    Option        "LockedDrags"        "0"    # If off, a tap and drag gesture ends when you release the finger. 
#...                            # If on, the gesture is active until you tap a second time or until LockedDragTimeout expires.
    Option        "LockedDragTimeout"    "5000"    # How long in ms for the LockedDrags mode to be automatically turned off after finger is released.
    Option        "CircularScrolling"    "false"    # If on, circular scrolling is used.
    Option        "CircScrollDelta"    "30"    # Move angle (radians) of finger to generate a scroll event.
    Option        "CircScrollTrigger"    "0"    # Trigger region on the touchpad to start circular scrolling.
#...                            # All Edges = 0. Top Edge = 1. Top Right Corner = 2. Right Edge = 3. Bottom Right Corner = 4.
#...                            # Bottom Edge = 5. Bottom Left Corner = 6. Left Edge = 7. Top Left Corner = 8.
    Option        "RTCornerButton"    "1"    # Which mouse button is reported on a right top corner tap. Set to 0 to disable.
    Option        "RBCornerButton"    "1"    # Which mouse button is reported on a right bottom corner tap. Set to 0 to disable.
    Option        "LTCornerButton"    "1"    # Which mouse button is reported on a left top corner tap. Set to 0 to disable.
    Option        "LBCornerButton"    "1"    # Which mouse button is reported on a left bottom corner tap. Set to 0 to disable.
    Option        "TapButton1"        "1"
    Option        "TapButton2"        "2"
    Option        "TapButton3"        "3"
    Option        "PalmDetect"        "true"    # If palm detection should be enabled.
    Option        "PalmMinWidth"        "10"    # Minimum finger width at which touch is considered a palm.
     Option        "PalmMinZ"        "200"    # Minimum finger pressure at which touch is considered a palm.
    Option        "GrabEventDevice"    "true"  # If true, no other user space or kernel space program sees the touchpad events. 
#...                            # This is desirable if the X config file includes /dev/input/mice as an input device.
#...                            # This is undesirable if you want to monitor the device from user space. 
    Option        "TapAndDragGesture"    "true" # Switch on/off the tap-and-drag gesture. The gesture is enabled by default.
    Option        "AreaLeftEdge"        "0"    # Ignore movements, scrolling and tapping which take place left of this edge.
    Option        "AreaRightEdge"        "0"    # Ignore movements, scrolling and tapping which take place right of this edge. 
    Option        "AreaTopEdge"        "0"    # Ignore movements, scrolling and tapping which take place above this edge.
    Option        "AreaBottomEdge"    "0"    # Ignore movements, scrolling and tapping which take place below this edge. 
    Option        "JumpyCursorThreshold"    "100"    # Set the threshold above which movement events are ignored on single-touch touchpads. 
#...                            # This option is disabled by default.
EndSection

Section "InputClass"
    Identifier "Dell Inspiron embedded buttons quirks"
    MatchTag "inspiron_1011|inspiron_1012"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection
root@aa-i3:~# 

```

and then reboot the laptop.

The above change resulted in the touchpad being completely disabled!!!
So, I had to use the USB live stick with ubuntu 10.04 (created sometime ago), which is an earlier kernel version:

```

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```

and I checked the mouse properties and DOES HAVE the tocuhpad option in the mouse settings...  Not great options, but at least something:

General
[ ] Dsiable touchpad while typeing
[ ] Enable mouse clicks with touchpad

Scrolling
<two options>

So now under this live stick i see that the relevant files and outputs are:

```

ubuntu@ubuntu:~$ cat /usr/lib/X11/xorg.conf.d/10-synaptics.conf
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron embedded buttons quirks"
    MatchTag "inspiron_1011|inspiron_1012"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection
ubuntu@ubuntu:~$ 

```

then the xinput says:

```

ubuntu@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
ubuntu@ubuntu:~$ 

```

and for the specific id:

```

ubuntu@ubuntu:~$ xinput list-props 12
Device 'AlpsPS/2 ALPS GlidePoint':
    Device Enabled (118):    1
    Device Accel Profile (234):    0
    Device Accel Constant Deceleration (235):    1.000000
    Device Accel Adaptive Deceleration (237):    1.000000
    Device Accel Velocity Scaling (238):    10.000000
    Synaptics Edges (239):    153, 870, 115, 652
    Synaptics Finger (240):    12, 14, 127
    Synaptics Tap Time (241):    180
    Synaptics Tap Move (242):    56
    Synaptics Tap Durations (243):    180, 180, 100
    Synaptics Tap FastTap (244):    0
    Synaptics Middle Button Timeout (245):    75
    Synaptics Two-Finger Pressure (246):    139
    Synaptics Two-Finger Width (247):    7
    Synaptics Scrolling Distance (248):    25, 25
    Synaptics Edge Scrolling (249):    1, 0, 0
    Synaptics Two-Finger Scrolling (250):    0, 0
    Synaptics Move Speed (251):    0.400000, 0.700000, 0.039124, 40.000000
    Synaptics Edge Motion Pressure (252):    14, 79
    Synaptics Edge Motion Speed (253):    1, 102
    Synaptics Edge Motion Always (254):    0
    Synaptics Button Scrolling (255):    1, 1
    Synaptics Button Scrolling Repeat (256):    1, 1
    Synaptics Button Scrolling Time (257):    100
    Synaptics Off (258):    1
    Synaptics Guestmouse Off (259):    0
    Synaptics Locked Drags (260):    0
    Synaptics Locked Drags Timeout (261):    5000
    Synaptics Tap Action (262):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (263):    1, 1, 1
    Synaptics Circular Scrolling (264):    0
    Synaptics Circular Scrolling Distance (265):    0.100000
    Synaptics Circular Scrolling Trigger (266):    0
    Synaptics Circular Pad (267):    0
    Synaptics Palm Detection (268):    0
    Synaptics Palm Dimensions (269):    10, 99
    Synaptics Coasting Speed (270):    0.000000
    Synaptics Pressure Motion (271):    14, 79
    Synaptics Pressure Motion Factor (272):    1.000000, 1.000000
    Synaptics Grab Event Device (273):    1
    Synaptics Gestures (274):    1
    Synaptics Capabilities (275):    1, 1, 1, 0, 0
    Synaptics Pad Resolution (276):    1, 1
    Synaptics Area (277):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (278):    0
ubuntu@ubuntu:~$ 

```

and for id=13:

```

ubuntu@ubuntu:~$ xinput list-props 13
Device 'PS/2 Mouse':
    Device Enabled (118):    1
    Device Accel Profile (234):    0
    Device Accel Constant Deceleration (235):    1.000000
    Device Accel Adaptive Deceleration (237):    1.000000
    Device Accel Velocity Scaling (238):    10.000000
    Evdev Reopen Attempts (233):    10
    Evdev Axis Inversion (280):    0, 0
    Evdev Axes Swap (282):    0
    Axis Labels (283):    "Rel X" (126), "Rel Y" (127)
    Button Labels (284):    "Button Left" (119), "Button Middle" (120), "Button Right" (121), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Middle Button Emulation (285):    2
    Evdev Middle Button Timeout (286):    50
    Evdev Wheel Emulation (287):    0
    Evdev Wheel Emulation Axes (288):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (289):    10
    Evdev Wheel Emulation Timeout (290):    200
    Evdev Wheel Emulation Button (291):    4
    Evdev Drag Lock Buttons (292):    0
ubuntu@ubuntu:~$ 

```

and for id=14

```

ubuntu@ubuntu:~$ xinput list-props 14
Device 'Macintosh mouse button emulation':
    Device Enabled (118):    1
    Device Accel Profile (234):    0
    Device Accel Constant Deceleration (235):    1.000000
    Device Accel Adaptive Deceleration (237):    1.000000
    Device Accel Velocity Scaling (238):    10.000000
    Evdev Reopen Attempts (233):    10
    Evdev Axis Inversion (280):    0, 0
    Evdev Axes Swap (282):    0
    Axis Labels (283):    "Rel X" (126), "Rel Y" (127)
    Button Labels (284):    "Button Left" (119), "Button Middle" (120), "Button Right" (121), "Button Wheel Up" (122), "Button Wheel Down" (123)
    Evdev Middle Button Emulation (285):    2
    Evdev Middle Button Timeout (286):    50
    Evdev Wheel Emulation (287):    0
    Evdev Wheel Emulation Axes (288):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (289):    10
    Evdev Wheel Emulation Timeout (290):    200
    Evdev Wheel Emulation Button (291):    4
    Evdev Drag Lock Buttons (292):    0
ubuntu@ubuntu:~$ 

```


Since I can not now work under live stick (do not have cable internet connection and can not load the WiFi driver, typing this into a file and then will post), then i am going now to replace the 
 10-synaptics.conf file created previously (- where the line was commented out which caused the touchpad and attached USB mouse compeltely disabled, so i can not lod in.)

I am doing:

(copying current settings under LIVE ubuntu USB stick to teh settings on the harddrive lond number starting with 588... is the name of the harddrive i guess)
```

ubuntu@ubuntu:~$ sudo cp /usr/lib/X11/xorg.conf.d/10-synaptics.conf /media/5886de99-e40d-4a01-b093-18a530938d33/usr/lib/X11/xorg.conf.d/10-synaptics.conf

```

now checking:

```

ubuntu@ubuntu:~$ cat /media/5886de99-e40d-4a01-b093-18a530938d33/usr/lib/X11/xorg.conf.d/10-synaptics.conf
Section "InputClass"
    Identifier "touchpad catchall"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron embedded buttons quirks"
    MatchTag "inspiron_1011|inspiron_1012"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "90"
    Option "AreaBottomEdge" "4100"
EndSection

Section "InputClass"
    Identifier "Dell Inspiron quirks"
    MatchTag "inspiron_1120"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "250"
EndSection

Section "InputClass"
    Identifier "HP Mininote quirks"
    MatchTag "mininote_1000"
    MatchDevicePath "/dev/input/event*"
    Driver "synaptics"
    Option "JumpyCursorThreshold" "20"
EndSection
ubuntu@ubuntu:~$ 

```

now I am rebooting and will continue to edit this and then post...

...and what i see now is that my mouse preferences STILL DO NOT HAVE the touchpad.

Something interesting going on:  under LIVE USB it recognise the touchpad, then it stopped doing it...

Can you help please?

---

### Post by aa-hcl on 2010-09-21
> **aa-hcl said:**
> 
...
```

ubuntu@ubuntu:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
ubuntu@ubuntu:~$ 

```and for the specific id:
....



by comparing the above list obtained under ubuntu live with the current list:

```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
aa@aa-i3:~$ 

```

I can see that apparently I am missing the 

&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=12    [slave  pointer  (2)]

Any idea what do I need to change in order to enable this AlpsPS/2 device?

Many thanks!!!!

---

### Post by Ayuthia on 2010-09-21
From what I understand, to get that name changed, it will most likely be a kernel module update.  Here is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/505474") that brings up the same issue, but with a different model.

If you can spare a CD and some bandwidth, you might try creating a Maverick liveCD to see if it recognizes your device correctly (but don't install it).  If it doesn't, you might want to check to see if there is a bug report listed for your laptop.

When you have a chance, can you attach a copy of the dmesg.txt file:
```

cd
dmesg > dmesg.txt

```

Hopefully it will provide the information about your touchpad and we can verify if it is listed in the kernel module code.

---

### Post by aa-hcl on 2010-09-21
> **Ayuthia said:**
> ...

When you have a chance, can you attach a copy of the dmesg.txt file:
```

cd
dmesg > dmesg.txt

```Hopefully it will provide the information about your touchpad and we can verify if it is listed in the kernel module code.

the results of 

```

aa@aa-i3:~$ cd
aa@aa-i3:~$ dmesg > dmesg.txt
aa@aa-i3:~$ 

```

is attached.... Sorry can not attach: **dmesg.txt**:
		Your file of 60.4 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

Sorry... will change the file extention to odt... works..

Many thanks!

---

### Post by Ayuthia on 2010-09-21
I just saw your information about the USB live stick and was wondering if you have tried to drop back to 2.6.32-21-generic.  You might try that to see if the device shows up.

The other thing to check is to go back on the USB and check the /var/log/Xorg.0.log to see how it is picked up.  Also check the dmesg file to see how it is getting assigned there.

---

### Post by aa-hcl on 2010-09-21
> **Ayuthia said:**
> I just saw your information about the USB live stick and was wondering if you have tried to drop back to 2.6.32-21-generic.  You might try that to see if the device shows up.

The other thing to check is to go back on the USB and check the /var/log/Xorg.0.log to see how it is picked up.  Also check the dmesg file to see how it is getting assigned there.


Hi,

many thanks for suggestion - it does work with kernel 21.

now going towards 21 kernel (it is very wise that ubuntu offers booting previous kernels!!!!):

```

aa@aa-i3:~$ uname -a
Linux aa-i3 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```


```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
aa@aa-i3:~$ 

```

Now the touchpad is properly recognised as it is clear from the xinput - it is AlpsPS/2 one; in the mouse preferences there is the required touchpad (although primitive!!!) preferences.

Now let us see how it was picked up:

```

aa@aa-i3:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux aa-i3 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=5886de99-e40d-4a01-b093-18a530938d33 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 21 17:50:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0046:1028:0428 Intel Corporation Core Processor Integrated Graphics Controller rev 2, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00008080/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
(--) intel(0): Chipset: "Arrandale"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP3 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output DP1
(II) intel(0): Manufacturer: LGD  Model: 29e  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.4
(II) intel(0): Digital Display Input
(II) intel(0): 6 bits per channel
(II) intel(0): Digital interface is DisplayPort
(II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): Preferred mode is native pixel format and refresh rate
(II) intel(0): redX: 0.617 redY: 0.349   greenX: 0.314 greenY: 0.597
(II) intel(0): blueX: 0.151 blueY: 0.057   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 96.0 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1728 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 64.2 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1740 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 922 v_border: 0
(II) intel(0):  P727R&#65533;156WD1
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0030e49e0200000000
(II) intel(0):     0013010495221378021be59e59509826
(II) intel(0):     0e505400000001010101010101010101
(II) intel(0):     0101010101018025408060841a303020
(II) intel(0):     350058c2100000181419408c60841630
(II) intel(0):     3020350058c210000018000000fe0050
(II) intel(0):     37323752803135365744310a00000000
(II) intel(0):     00004131190000000009010a202000da
(II) intel(0): Printing probed modes for output DP1
(II) intel(0): Modeline "1600x900"x60.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x40.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP3
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output DP1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP3 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output DP1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
(**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_2M: always reports core events
(**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
(II) Laptop_Integrated_Webcam_2M: Found keys
(II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "enable synaptics SHMConfig"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "on"
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event6"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
aa@aa-i3:~$ 

```

and now putting:

```

aa@aa-i3:~$ dmesg > dmesg_kernel21.odt
aa@aa-i3:~$ 

```

and file dmesg_kernel21.odt is attached.

Although I can still boot into kernel 21, but it would be nice to work out how to do it properly!!!

Many thanks!!!

---

### Post by Ayuthia on 2010-09-21
> **aa-hcl said:**
> Hi,

many thanks for suggestion - it does work with kernel 21.

now going towards 21 kernel (it is very wise that ubuntu offers booting previous kernels!!!!):

```

aa@aa-i3:~$ uname -a
Linux aa-i3 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```


```

aa@aa-i3:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_2M                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=15    [slave  keyboard (3)]
aa@aa-i3:~$ 

```

Now the touchpad is properly recognised as it is clear from the xinput - it is AlpsPS/2 one; in the mouse preferences there is the required touchpad (although primitive!!!) preferences.

Now let us see how it was picked up:

```

aa@aa-i3:~$ cat /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux aa-i3 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=5886de99-e40d-4a01-b093-18a530938d33 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 21 17:50:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0046:1028:0428 Intel Corporation Core Processor Integrated Graphics Controller rev 2, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x00008080/8
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.9.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
(--) intel(0): Chipset: "Arrandale"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): Output HDMI2 has no monitor section
(II) intel(0): Output DP3 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output DP1
(II) intel(0): Manufacturer: LGD  Model: 29e  Serial#: 0
(II) intel(0): Year: 2009  Week: 0
(II) intel(0): EDID Version: 1.4
(II) intel(0): Digital Display Input
(II) intel(0): 6 bits per channel
(II) intel(0): Digital interface is DisplayPort
(II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): Preferred mode is native pixel format and refresh rate
(II) intel(0): redX: 0.617 redY: 0.349   greenX: 0.314 greenY: 0.597
(II) intel(0): blueX: 0.151 blueY: 0.057   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 96.0 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1728 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 64.2 MHz   Image Size:  344 x 194 mm
(II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1740 h_border: 0
(II) intel(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 922 v_border: 0
(II) intel(0):  P727R&#65533;156WD1
(II) intel(0): Unknown vendor-specific block 0
(II) intel(0): EDID (in hex):
(II) intel(0):     00ffffffffffff0030e49e0200000000
(II) intel(0):     0013010495221378021be59e59509826
(II) intel(0):     0e505400000001010101010101010101
(II) intel(0):     0101010101018025408060841a303020
(II) intel(0):     350058c2100000181419408c60841630
(II) intel(0):     3020350058c210000018000000fe0050
(II) intel(0):     37323752803135365744310a00000000
(II) intel(0):     00004131190000000009010a202000da
(II) intel(0): Printing probed modes for output DP1
(II) intel(0): Modeline "1600x900"x60.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x40.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP2
(II) intel(0): EDID for output HDMI2
(II) intel(0): EDID for output DP3
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output DP1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Output HDMI2 disconnected
(II) intel(0): Output DP3 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output DP1 using initial mode 1600x900
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 423 x 238
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Video Bus (/dev/input/event10)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event10"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Lid Switch (/dev/input/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
(**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
(**) Laptop_Integrated_Webcam_2M: always reports core events
(**) Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
(II) Laptop_Integrated_Webcam_2M: Found keys
(II) Laptop_Integrated_Webcam_2M: Configuring as keyboard
(II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event12)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event13)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel HP Out at Ext Front Jack (/dev/input/event14)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
(**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event8"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found relative axes
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(II) PS/2 Mouse: initialized for relative axes.
(II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
(**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "enable synaptics SHMConfig"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(**) Option "SHMConfig" "on"
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 0
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
(**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event6)
(**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
(**) Dell WMI hotkeys: always reports core events
(**) Dell WMI hotkeys: Device: "/dev/input/event6"
(II) Dell WMI hotkeys: Found keys
(II) Dell WMI hotkeys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
(II) intel(0): EDID vendor "LGD", prod id 670
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1600x900"x0.0   96.00  1600 1648 1680 1728  900 903 908 926 -hsync -vsync (55.6 kHz)
(II) intel(0): Modeline "1600x900"x0.0   64.20  1600 1648 1680 1740  900 903 908 922 -hsync -vsync (36.9 kHz)
aa@aa-i3:~$ 

```

and now putting:

```

aa@aa-i3:~$ dmesg > dmesg_kernel21.odt
aa@aa-i3:~$ 

```

and file dmesg_kernel21.odt is attached.

Although I can still boot into kernel 21, but it would be nice to work out how to do it properly!!!

Many thanks!!!
You might try gsynaptics.  I have never tried it though so I am not for sure about how well it works.  I have usually configured things through the xorg.conf.d files.  It is suppsoed to provide a better way to make adjustments to the touchpad.

As for the kernel, there must have been a patch that was applied to the kernel that broke the functionality for your device.  The best thing to do is to submit a [bug report]("https://help.ubuntu.com/community/ReportingBugs").  It might also be possible that the bug has been reported at launchpad.net so you might check there first.

At this point, if you want to use your touchpad you will need to use the -21-generic kernel and wait until the next kernel release is made and test it again.

---

### Post by johann.fridriksson on 2010-09-26
Hi!

I have the E5510 running 10.04 too.

What do you have installed in the mentioned USB stick? Distro, distro-version and kernel version?

Can you do an lsmod for us while running this USB-stick version of the kernel?

---

### Post by cfaber on 2010-10-21
Yes please, I'm interested as well

---

### Post by Fiery Spirited on 2010-10-31
Could you clearify what kind of functionality that you got working with this old kernel?

The reason I ask is that my research indicate that the problem with the Alps touchpad is two-fold. At one level the touchpad is incorrectly recognized as a PS2 mouse and not as a TouchPad. On the other hand the behavior is pretty rational in those cases when the Kernel encounter a TouchPad that uses a protocol that has still not been reverse engineered.

In the following Kernel discussion they are working to understand the protocol of new Alps TouchPads
[https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660)

There seems to be a patch developed together with Dell to get scrolling to work to some degree on at least some of the new Alps models. I am bit a hesistant to try that one since I am not very comfortable to patch the kernel. The lack of scrolling is not a big deal for me. Multitouch support would be a different thing.

The right launchpad issue for this problem is as far as I can tell btw [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/606238)

---

### Post by micdac on 2010-12-20
I have the same Problem with Dell e6410 and ubuntu 10.10 64bit. the trackpad is just recognized as a ps2-mouse. I am so far o.k with it, but I would like to turn off the touchpad during typing. Which of the several workarounds I should try? I just need to define a Shortkey for Turn-on-off. Thanks

---

### Post by aa-hcl on 2011-01-02
Hi, sorry for the delay with answer.

I did the following:

(see [https://bugzilla.kernel.org/show_bug.cgi?id=14660](https://bugzilla.kernel.org/show_bug.cgi?id=14660))

I have downloaded the script and attached it to "Win+z" shortcut through the terminal (to do so just go System -> Preferences -> Keyboard shortcuts; "Win" is the windows key on the keyboard):  "xterm /home/YourUsename/toggleps2.sh"  and it works!!! it disables the touchpad and I can use the external mouse!!!!

the script that i got from the above links is:

:~$ cat ./toggleps2.sh 
#!/bin/bash

state=`xinput --list-props "PS/2 Generic Mouse" | grep Enabled | awk '{print $4}'`
#echo "state = "$state;

if [ $state = '1' ]
then
    xinput --set-prop --type=int --format=8 "PS/2 Generic Mouse" "Device Enabled" "0"
else
    xinput --set-prop --type=int --format=8 "PS/2 Generic Mouse" "Device Enabled" "1"
fi


This helps with the external mouse attached.

BUT:  I ALSO WANT SOLUTION WHEN THE TOUCHPAD is properly recognised by ubuntu; this seems to be ongoing issue.

---

