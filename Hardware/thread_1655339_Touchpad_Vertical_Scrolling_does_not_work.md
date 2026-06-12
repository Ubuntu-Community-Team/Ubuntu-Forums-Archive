---
title: "Touchpad Vertical Scrolling does not work"
date: 2010-12-29
forum: Hardware
---

### Post by WthIteh on 2010-12-29
On the Ideapa Z360 with Ubuntu 10.10 and kernel 2.6.35-24-generic my touchpad
vertical scrolling does not work. All other features of it like tapping, dragging, etc. work well. But no vertical scrolling.

It is detected in *xinput --list* as *PS/2 Generic Mouse* instead of touchpad too.

Any idea?

---

### Post by pi/roman on 2010-12-29
hello, try this in terminal

```
synclient vertedgescroll=1
```

---

### Post by WthIteh on 2010-12-30
Thanks for the reply.
I used
```
synclient vertedgescroll=1
```and it said
```
Couldn't find synaptics properties. No synaptics driver loaded?
```
Any idea?

---

### Post by WthIteh on 2010-12-30
Looking for ideas..... :-?

---

### Post by pi/roman on 2010-12-30
It's strange because I believe you do have a synaptics touchpad although the synaptics driver doesn't appear to be loaded.  You should check your log to see what is happening, try this:
```
cat /var/log/Xorg.0.log | grep -i touchpad
```

---

### Post by WthIteh on 2010-12-31
> **pi/roman said:**
> It's strange because I believe you do have a synaptics touchpad although the synaptics driver doesn't appear to be loaded.  You should check your log to see what is happening, try this:
```
cat /var/log/Xorg.0.log | grep -i touchpad
```
I believe that it must be a synaptics one and detected somehow behind the scene. Since all of its features like tap-and-drag, etc. else of vertical scrolling works.
I tried
```
cat /var/log/Xorg.0.log | grep -i touchpad
```And output was **empty**. I checked */var/log/Xorg.0.log* log file more carefully and the only related part in it was
```

[    75.181] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    75.181] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    75.181] (**) PS/2 Generic Mouse: always reports core events
[    75.181] (**) PS/2 Generic Mouse: Device: "/dev/input/event7"
[    75.211] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    75.211] (II) PS/2 Generic Mouse: Found relative axes
[    75.211] (II) PS/2 Generic Mouse: Found x and y relative axes
[    75.211] (II) PS/2 Generic Mouse: Configuring as mouse
[    75.211] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    75.211] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    75.211] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    75.211] (II) PS/2 Generic Mouse: initialized for relative axes.
[    75.211] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    75.211] (II) No input driver/identifier specified (ignoring)

```Which detects touchpad as PS/2 Generic Mouse.

And here is output of **xinput** for this device:
```

Device 'PS/2 Generic Mouse':
    Device Enabled (125):    1
    Coordinate Transformation Matrix (127):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (244):    0
    Device Accel Constant Deceleration (245):    1.000000
    Device Accel Adaptive Deceleration (246):    1.000000
    Device Accel Velocity Scaling (247):    10.000000
    Evdev Reopen Attempts (242):    10
    Evdev Axis Inversion (248):    0, 0
    Evdev Axes Swap (250):    0
    Axis Labels (251):    "Rel X" (135), "Rel Y" (136)
    Button Labels (252):    "Button Left" (128), "Button Middle" (129), "Button Right" (130), "Button Wheel Up" (131), "Button Wheel Down" (132)
    Evdev Middle Button Emulation (253):    2
    Evdev Middle Button Timeout (254):    50
    Evdev Wheel Emulation (255):    0
    Evdev Wheel Emulation Axes (256):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (257):    10
    Evdev Wheel Emulation Timeout (258):    200
    Evdev Wheel Emulation Button (259):    4
    Evdev Drag Lock Buttons (260):    0

```I found in other sites that **synclient** needs **SHM** enabled and enabling SHM requires **fdi** config under */etc/hal*, but in my system there is no /etc/hal at all! Maybe related!?

And this is the result of an *aptitude search* for synaptics. It seems that the driver is installed.
```
i   xserver-xorg-input-synaptics                                                - Synaptics TouchPad driver for X.Org server                                           

```What should I do now?

---

### Post by WthIteh on 2011-01-01
Looking for ideas yet......

---

### Post by WthIteh on 2011-01-02
> **WthIteh said:**
> Looking for ideas yet......
Please help with this issue..... What could I do to solve it?

---

### Post by aa-hcl on 2011-01-02
I have the same problem on my dell E5510. This problem (i.e. touchpad is recognised as ordinary mouse) has been around for a while, so it would be nice if the solution is found.

Interesting, but in older version of ubuntu (10.04) the problem did not exist.

---

### Post by pi/roman on 2011-01-02
Thanks for taking the initiative in finding the relevant xorg log data. It looks like your touchpad is being picked up entirely by the evdev driver. I made a suggestion on a similar matter in another thread that I still haven't seen a reply on so I'm not really sure if it will work. This will involve editing your xorg.conf so you shoud be sure to have a live cd handy so you can go in and fix it if you make a mistake.

Open up your xorg.conf in an editor and in the "ServerLayout" section add this line:
```
InputDevice    "Touchpad"  "CorePointer"
```"Touchpad" will be your somewhat arbitrary identifier so it must match in the next section but you can use any identifier you want as long as it matches.

Now create a new "InputDevice" section
```
Section "InputDevice"
    Driver        "synaptics"
    Identifier    "Touchpad"
EndSection
```The synaptics driver should be assigned to your touchpad. Save that and reboot. If it won't boot properly then there is something wrong with it and you need to use the live cd to go in and edit it.

---

### Post by aa-hcl on 2011-01-02
Hi,

on my dell E5510 i have the same and I am going to try your solution now... But I will go and find my live CD or live USB just in case.... I will then post the results...

---

### Post by WthIteh on 2011-01-02
My current xorg.conf file content is as:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        InputDevice     "Touchpad"      "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Touchpad"
        Driver          "synaptics"
EndSection

```
After reboot, nothing changed.
I checked the logs and no change was there too.

Previously I had no xorg.conf at all. I created that file (/etc/X11/xorg.conf) with above content. Maybe it is not used by X11!? Any work required to enable it?

---

### Post by aa-hcl on 2011-01-02
My current xorg.conf file is:

[CODE]
root@aa-i3:~# cat /etc/X11/xorg.conf 
Section "InputClass"
        Identifier "enable synaptics SHMConfig"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "SHMConfig" "on"
EndSection
root@aa-i3:~# 
[\CODE]

what should I do?

---

### Post by aa-hcl on 2011-01-02
> **WthIteh said:**
> My current xorg.conf file content is as:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        InputDevice     "Touchpad"      "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Touchpad"
        Driver          "synaptics"
EndSection

```After reboot, nothing changed.
I checked the logs and no change was there too.

Previously I had no xorg.conf at all. I created that file (/etc/X11/xorg.conf) with above content. Maybe it is not used by X11!? Any work required to enable it?


I did not know where is my xorg.conf and looked at Xorg.0.log and it says:

[CODE]
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  2 13:29:12 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
[\CODE]

so, i presume it does read this file?

---

### Post by WthIteh on 2011-01-02
> **aa-hcl said:**
> I did not know where is my xorg.conf and looked at Xorg.0.log and it says:

[CODE]
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  2 13:29:12 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
[\CODE]

so, i presume it does read this file?
Yes, the path (/etc/X11/xorg.conf) is correct. But as I know the xorg.conf is obsolete. So maybe it was not used!! I don't know.

---

### Post by WthIteh on 2011-01-02
> **aa-hcl said:**
> I did not know where is my xorg.conf and looked at Xorg.0.log and it says:

[CODE]
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan  2 13:29:12 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
[\CODE]

so, i presume it does read this file?
 Yes, the path (/etc/X11/xorg.conf) is correct. But as I know the xorg.conf is obsolete. So maybe it was not used!! I don't know.

---

### Post by aa-hcl on 2011-01-02
I have now rebooted and with modified xorg.conf:

[CODE]
aa@aa-i3:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
        Identifier      "Default Layout"
        InputDevice     "Touchpad"      "CorePointer"
EndSection

Section "InputDevice"
        Identifier      "Touchpad"
        Driver          "synaptics"
EndSection
[\CODE]

the touchpad is still an ordinary mouse.  I guess my previous version of xorg.conf was the old attempt to fix the same problem.

It would be really nice if the solution is found!

---

### Post by pi/roman on 2011-01-02
This configuration was missing a quotation mark, now fixed.

Both configurations are being used. I like to keep all my changes separate though so they are easy to find and adjust without messing with the originals.  I think this configuration might work.

```
Section "ServerLayout"
    Identifier "Default Layout"
    InputDevice "Touchpad" "CorePointer"
    InputDevice "Mouse" "SendCoreEvents" "on"
EndSection

Section "InputDevice"
    Identifier "Mouse"
    Driver "mouse"
    Option "Protocol" "auto"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier "Touchpad"
    Driver     "synaptics"
   Option "Protocol" "auto-dev"
   Option "Device" "/dev/evdev"
EndSection
```After rebooting run the following command to check what happened in the log.

```
cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad'
```

---

### Post by logangorence on 2011-01-02
Try System -> Prefences -> Mouse -> Touchpad -> Set Edge Scrolling and Vertical Scrolling and Click Close.:p

---

### Post by WthIteh on 2011-01-02
> **pi/roman said:**
> This configuration was missing a quotation mark, now fixed.

Both configurations are being used. I like to keep all my changes separate though so they are easy to find and adjust without messing with the originals.  I think this configuration might work.

```
Section "ServerLayout"
    Identifier "Default Layout"
    InputDevice "Touchpad" "CorePointer"
    InputDevice "Mouse" "SendCoreEvents" "on"
EndSection

Section "InputDevice"
    Identifier "Mouse"
    Driver "mouse"
    Option "Protocol" "auto"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier "Touchpad"
    Driver     "synaptics"
   Option "Protocol" "auto-dev"
   Option "Device" "/dev/evdev"
EndSection
```After rebooting run the following command to check what happened in the log.

```
cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad'
```
With the given xorg.conf I get in Xorg.0.log file:
```

[    58.481] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    58.481] (**) PS/2 Generic Mouse: Applying InputClass "**evdev pointer catchall**"
[    58.481] (**) PS/2 Generic Mouse: always reports core events
[    58.481] (**) PS/2 Generic Mouse: Device: "/dev/input/event7"
[    58.601] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    58.601] (II) PS/2 Generic Mouse: Found relative axes
[    58.601] (II) PS/2 Generic Mouse: Found x and y relative axes
[    58.601] (II) PS/2 Generic Mouse: Configuring as mouse
[    58.601] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    58.601] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    58.601] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    58.601] (II) PS/2 Generic Mouse: initialized for relative axes.
[    58.601] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    58.601] (II) **No input driver/identifier specified** (ignoring)

```
It seems that "**evdev pointer catchall**" has precedence to above xorg.conf settings. Maybe we need a line in xorg.conf for overriding it!? BTW, it detect touchpad as PS/2 Generic Mouse yet.

---

### Post by WthIteh on 2011-01-02
> **logangorence said:**
> Try System -> Prefences -> Mouse -> Touchpad -> Set Edge Scrolling and Vertical Scrolling and Click Close.:p
There is no *Touchpad* tab in the *System -> Prefences -> Mouse* window.

---

### Post by aa-hcl on 2011-01-02
interesting, but my results are different. It is still the case that my touchpad is an ordinary mouse unfortunately.

so i did change the xorg.conf file as recommended:

[code]
root@aa-i3:~# cat /etc/X11/xorg.conf
Section "ServerLayout"
    Identifier "Default Layout"
    InputDevice "Touchpad" "CorePointer"
    InputDevice "Mouse" "SendCoreEvents" "on"
EndSection

Section "InputDevice"
    Identifier "Mouse"
    Driver "mouse"
    Option "Protocol" "auto"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier "Touchpad"
    Driver     "synaptics"
   Option "Protocol" "auto-dev"
   Option "Device" "/dev/evdev"
EndSection
root@aa-i3:~# 
[\code]

rebooted and then checked:

[code]
aa@aa-i3:~$ cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad'
(**) |-->Input Device "Touchpad"
(**) |-->Input Device "Mouse"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse
(==) intel(0): Silken mouse enabled
(II) Synaptics touchpad driver version 1.2.2
Touchpad no synaptics event device found
(EE) PreInit failed for input device "Touchpad"
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
(II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
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
aa@aa-i3:~$ 
[\code]

you can see in the above that it was trying to use touchpad driver, but PreInit failed...

Any suggestions?

Many thanks!

---

### Post by pi/roman on 2011-01-03
It may be a day or two before i get back to this but could you please post the output of the following, installing hwinfo if necessary.

```
hwinfo --mouse
```

---

### Post by WthIteh on 2011-01-03
> **pi/roman said:**
> It may be a day or two before i get back to this but could you please post the output of the following, installing hwinfo if necessary.

```
hwinfo --mouse
```
Here is the output:
```

> hal.1: read hal dataprocess 5668: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
36: PS/2 00.0: 10500 PS/2 Mouse                                 
  [Created at input.183]
  Unique ID: AH6Q.U5GX9Ignjc0
  Hardware Class: mouse
  Model: "PS/2 Generic Mouse"
  Vendor: 0x0002 
  Device: 0x0001 "PS/2 Generic Mouse"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event7, /dev/char/13:71, /dev/input/by-path/platform-i8042-serio-4-event-mouse, /dev/char/13:32, /dev/input/by-path/platform-i8042-serio-4-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
The first line in this output is suspicious.
```

> hal.1: read hal dataprocess 5668: arguments to dbus_move_error()  were incorrect, assertion "(dest) == NULL || !dbus_error_is_set  ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

```
Maybe disabled "Hal" prevent correct detection?

---

### Post by aa-hcl on 2011-01-03
I did not have hwinfo, installing through Synaptics... done. now posting the results:

```

aa@aa-i3:~$ hwinfo --mouse
41: ADB 00.0: 10502 Bus Mouse                                   
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/computer_logicaldev_input_3
  Unique ID: kZYT.VdKNesd9pT6
  Hardware Class: mouse
  Model: "Macintosh mouse button emulation"
  Vendor: 0x0001 
  Device: 0x0001 "Macintosh mouse button emulation"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/char/13:68, /dev/char/13:32, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

43: PS/2 00.0: 10500 PS/2 Mouse
  [Created at input.183]
  UDI: /org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input
  Unique ID: AH6Q.U5GX9Ignjc0
  Hardware Class: mouse
  Model: "PS/2 Generic Mouse"
  Vendor: 0x0002 
  Device: 0x0001 "PS/2 Generic Mouse"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event9, /dev/char/13:73, /dev/input/by-path/platform-i8042-serio-1-event-mouse, /dev/char/13:33, /dev/input/by-path/platform-i8042-serio-1-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:33)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
aa@aa-i3:~$ 

```

---

### Post by WthIteh on 2011-01-05
What is the next step?

---

### Post by aa-hcl on 2011-01-05
Hi,

May be we have not Synpatics touchpad, but need other driver, something like  AlpsPS/2 ALPS?

see 

[http://ubuntuforums.org/showthread.php?t=1593098&highlight=touchpad+dell](http://ubuntuforums.org/showthread.php?t=1593098&highlight=touchpad+dell)

---

### Post by aa-hcl on 2011-01-05
It looks like that in my case Synpatics driver was loaded, but it was unable to use the touchpad:

```

aa@aa-i3:~$ cat /var/log/Xorg.0.log | grep -i synaptics
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 1.2.2
Touchpad no synaptics event device found
(EE) Synaptics driver unable to open device
(II) UnloadModule: "synaptics"

```

The above probably shows that I have ALPS touchpad ???

Can you please tell me then how to loads the correct driver ???

Many thanks!

---

### Post by pi/roman on 2011-01-05
Your right, it is an Alps touchpad.  Lenovo falsely had it listed as synaptics in their product specifications.   There are some devs that are working on kernel patches for these touchpads and others but I'm not really sure if you should try any of those as your touchpad is supposed to work with the latest release of the synaptics driver. It would be a good idea to double check to see that your driver is updated.

Here is a replacement for the "Touchpad" input device section.  You need to remove the "InputDevice" section from xorg.conf i gave you earlier and use this one instead.  The added protocol and device by-path options will hopefully direct the synaptics driver to your touchpad. The updownscrolling should give Alps touchpads vertical scrolling but you will probably have it anyway if you can just get it to use the synaptics driver.

```
Section "InputDevice"
    Identifier "Touchpad"
    Driver     "synaptics"
    Option "Protocol" "alps"
    Option "Device" "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
    Option "UpDownScrolling" "1"   
EndSection
```The previous configuration was for Wthlteh,
aahcl, you should use the following configuration because the device path is different.

```
Section "InputDevice"
    Identifier "Touchpad"
    Driver     "synaptics"
    Option "Protocol" "alps"
    Option "Device" "/dev/input/by-path/platform-i8042-serio-1-event-mouse"
    Option "UpDownScrolling" "1"   
EndSection
```Make sure the identifier still matches the device in the "ServerLayout" section.  The protocol "alps" should work, but I would also like you to try this if you could:
```
    Option "Protocol" "auto"
```It seems like the kernel is refusing to acknowledge this device is not a mouse so it may be necessary to disable the auto detection of all pointing devices which is not a long term solution but it may help to locate a proper solution.

After rebooting could you run this to hopefully see that there were some changes in the touchpad device detection.
```
cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'
```

---

### Post by WthIteh on 2011-01-06
Very thanks for your help :D
I first tried
```
Option "Protocol" "auto"
```but it had no effect. Then I tried
```
Option "Protocol" "alps"
```and it detected touchpad device.
Here is output of the *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* command:
```

[   301.029] (**) |-->Input Device "Touchpad"
[   301.029] (**) |-->Input Device "Mouse"
[   301.030] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   301.030] (WW) Disabling Mouse
[   301.039] (II) LoadModule: "synaptics"
[   301.040] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   301.057] (II) Module synaptics: vendor="X.Org Foundation"
[   301.128] (==) intel(0): Silken mouse enabled
[   301.208] (II) Synaptics touchpad driver version 1.2.2
[   301.208] (**) Option "Device" "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
[   301.510] (**) Option "CorePointer"
[   301.510] (**) Touchpad: always reports core events
[   301.592] (II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
[   301.592] (**) Touchpad: (accel) keeping acceleration scheme 1
[   301.592] (**) Touchpad: (accel) acceleration profile 0
[   301.592] (**) Touchpad: (accel) acceleration factor: 2.000
[   301.592] (**) Touchpad: (accel) acceleration threshold: 4
[   302.403] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[   302.403] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[   302.403] (**) PS/2 Generic Mouse: always reports core events
[   302.403] (**) PS/2 Generic Mouse: Device: "/dev/input/event7"
[   302.482] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[   302.482] (II) PS/2 Generic Mouse: Found relative axes
[   302.482] (II) PS/2 Generic Mouse: Found x and y relative axes
[   302.482] (II) PS/2 Generic Mouse: Configuring as mouse
[   302.482] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[   302.482] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   302.482] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[   302.482] (II) PS/2 Generic Mouse: initialized for relative axes.
[   302.483] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)

```Very nice :D

But "vertical-scrolling" does not work yet. Also "tap", "tap-and-drag", "click", and "click-and-drag" features **are disabled too**!! And moving mouse-cursor on the screen after some seconds could cause wrong mouse location detection too. And mouse-cursor moves to corners of the screen. And it return under control after some seconds.

Here is my xorg.conf which detects touchpad but with above issues:
```


Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
    InputDevice    "Mouse"        "SendCoreEvents"    "on"
EndSection

Section "InputDevice"
    Identifier    "Mouse"
    Driver        "mouse"
    Option        "Protocol"    "auto"
    Option        "Device"    "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Protocol"    "alps"
    Option        "Device"    "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
    Option        "UpDownScrolling"    "1"
EndSection

```
I forced to comment "touchpad" line from xorg.conf to enable my mouse and come here.

Did I missed anything? It is alps and could be detected which is a good improvement. Does it need any training to learn correct button events?

---

### Post by pi/roman on 2011-01-06
I believe your mouse cursor may be moving around erratically because it is being operated by 2 drivers at the same time.  After booting up with the alps driver loaded and the cursor is jumping around, open up a terminal by pressing alt/f2 and running "gnome-terminal" then in terminal check out the xinput list and you will probably need to disable the mouse driver on the touchpad:

```
xinput set-prop 'PS/2 Generic Mouse' 'Device Enabled' 0
```

---

### Post by WthIteh on 2011-01-06
> **pi/roman said:**
> I believe your mouse cursor may be moving around erratically because it is being operated by 2 drivers at the same time.  After booting up with the alps driver loaded and the cursor is jumping around, open up a terminal by pressing alt/f2 and running "gnome-terminal" then in terminal check out the xinput list and you will probably need to disable the mouse driver on the touchpad:

```
xinput set-prop 'PS/2 Generic Mouse' 'Device Enabled' 0
```
Here are two experiments:
First: Using the previously said xorg.conf with line
```
Option  "Device"    "/dev/input/by-path/platform-i8042-serio-4-event-mouse
```
after reboot I disabled the extra auto-loaded driver by
```
xinput set-prop 'PS/2 Generic Mouse' 'Device Enabled' 0
```
and checked it by *xinput* command. There was Touchpad detected and PS/2 Generic Mouse disabled. But then I could not move mouse at all.
It seems that the event device of PS/2 which was the same as /dev/input/by-path/platform-i8042-serio-4-event-mouse was disabled with PS/2 Generic Mouse too.

Second: So I replaced that line in xorg.conf with
```
Option  "Device"    "/dev/input/by-path/platform-i8042-serio-4-mouse
```
and after reboot disabled PS/2 Generic Mouse.
This time (1) Touchpad was detected in xinput (2) and mouse movement works as before (with its features like tap, etc.) else of *vertical scrolling* feature.

Should I use /dev/input/by-path/platform-i8042-serio-4-event-mouse path?
   then how disable PS/2 without disabling touchpad too!?
or /dev/input/by-path/platform-i8042-serio-4-mouse path?
  then vertical scrolling does not work....

Many Thanks :)

---

### Post by pi/roman on 2011-01-06
Ok let's try this then to make the touchpad register for event7 as is listed in your hwinfo --mouse output. Open /etc/X11/xorg.conf and adjust the device line in the "Touchpad" section:
```
    Option "Device" "/dev/input/event7"
```then for the mouse auto-detection change the event code to register everything except 7.  Open /usr/share/X11/xorg.conf.d/10-evdev.conf
```
gksudo gedit /usr/share/X11/xorg.conf.d/10-evdev.conf
```it should look like this initially:

> # Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSectionthen change the pointer catch-all to look like this:
```

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event[^7]"
        Driver "evdev"
EndSection
```which will tell it to register every event except for 7 leaving that open for the "touchpad" configuration in xorg.conf.

---

### Post by WthIteh on 2011-01-06
Doing so, mouse completely disabled :-k
And this is the *xinput --list* output after reboot:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```And this is xorg.conf file:
```

Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
    InputDevice    "Mouse"        "SendCoreEvents"    "on"
EndSection

Section "InputDevice"
    Identifier    "Mouse"
    Driver        "mouse"
    Option        "Protocol"    "auto"
    Option        "Device"    "/dev/input/mice"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Protocol"    "alps"
    Option        "Device"    "/dev/input/event7"
    Option        "UpDownScrolling"    "1"
EndSection

```And this is /usr/share/X11/xorg.conf.d/10-evdev.conf file:
```

#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event[^7]"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

```
Do I miss any step?

---

### Post by pi/roman on 2011-01-06
You didn't miss anything. It should have worked. Back to googling and brainstorming I guess.

You could try some different protocols like "auto-dev" or "exps2".

Also if evdev is required to enable your touchpad you should probably change the 10-evdev.conf device line back the way it was to 'MatchDevicePath "/dev/input/event*"'.  Maybe there is a way to work with it and not get the erratic cursor movement.

I'm still thinking on it and come back if I have any ideas.

---

### Post by pi/roman on 2011-01-06
How about another swing at it. Note that this is risky territory because you could lose the use of your keyboard which means you would then have to boot up from live cd and change these settings back.

 For /usr/share/X11/xorg.conf.d/10-evdev.conf try this in place of the pointer catchall section which is the same as we tried earlier.

```
Section "InputClass"         
Identifier "evdev pointer catchall"         
MatchIsPointer "on"         
MatchDevicePath "/dev/input/event[^7]"         
Driver "evdev" 
EndSection
```Then for /usr/share/X11/xorg.conf.d/50-synaptics.conf in order to assign it to an input class remove the matchistouchpad and give it a path to your touchpad event.
```

Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchDevicePath "/dev/input/event7"
EndSection
```And in /etc/X11/xorg.conf, same as before along with including the input device identifier in the "serverlayout" section

```
Section "InputDevice"
     Identifier    "Touchpad"
     Driver        "synaptics"
     Option        "Protocol"    "alps"
     Option        "Device"    "/dev/input/event7"
     Option        "UpDownScrolling"    "1"
 EndSection
```The only difference here from what we tried before is the change to 50-synaptics.conf which I'm hoping will assign your touchpad to the correct input class since the pointer catchall is nullified for your touchpad.

---

### Post by pi/roman on 2011-01-06
Also along with the changes in my previous post this change should be included to  /usr/share/X11/xorg.conf.d/10-evdev.conf in the touchpad inputclass section. remove the matchistouchpad option and direct it to your touchpad event.

```
Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchDevicePath "/dev/input/event7"
        Driver "evdev"
EndSection
```

---

### Post by aa-hcl on 2011-01-06
Hi,

I tried the xorg.conf change as you proposed earlier (after realising that it is ALPS touchpad).

The touchpad was registered as touchpad, but it was also giving me two more mouse devices: Ps/2 and macintosh simulations. Sorry - no xinput results for this since the mouse was really bad: normal click did not work, I only was able to open the terminal manually the xorg.conf back and reboot....

i will try more and also to follow your more recent recommendations next day...

i would also want to do the following experiment:

I know that if booting from older version liveCD i was getting the touchpad detected and everything was fine. I now want to get all the configuration files from that boot to get a clue how the touchpad was detected.

Many thanks!

---

### Post by WthIteh on 2011-01-07
> **pi/roman said:**
> Also along with the changes in my previous post this change should be included to  /usr/share/X11/xorg.conf.d/10-evdev.conf in the touchpad inputclass section. remove the matchistouchpad option and direct it to your touchpad event.

```
Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchDevicePath "/dev/input/event7"
        Driver "evdev"
EndSection
```
It will disable mouse too. After reboot this is output
of *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* command:
```

[    59.349] (**) |-->Input Device "Touchpad"
[    59.349] (**) |-->Input Device "Mouse"
[    59.349] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    59.349] (WW) Disabling Mouse
[    59.373] (II) LoadModule: "synaptics"
[    59.373] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    59.385] (II) Module synaptics: vendor="X.Org Foundation"
[    59.451] (==) intel(0): Silken mouse enabled
[    59.516] (II) Synaptics touchpad driver version 1.2.2
[    60.023] (--) Touchpad: no supported touchpad found
[    60.023] (EE) Touchpad Unable to query/initialize Synaptics hardware.
[    60.143] (EE) PreInit failed for input device "Touchpad"
[    60.143] (II) UnloadModule: "synaptics"
[    60.461] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    60.461] (**) PS/2 Generic Mouse: Applying InputClass "evdev touchpad catchall"
[    60.461] (**) PS/2 Generic Mouse: Applying InputClass "touchpad catchall"
[    60.461] (II) Synaptics touchpad driver version 1.2.2
[    60.741] (--) PS/2 Generic Mouse: no supported touchpad found
[    60.741] (EE) PS/2 Generic Mouse Unable to query/initialize Synaptics hardware.
[    60.931] (EE) PreInit failed for input device "PS/2 Generic Mouse"
[    60.931] (II) UnloadModule: "synaptics"
[    60.931] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)

```
And this is result of *xinput --list* command:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```

I also tried different combinations of evdev and synaptics (in 10-evdev.conf and 50-synaptics.conf files) but in each case either (1) mouse was disabled or (2) it was operated by both Touchpad Synaptics and PS/2 Generic Mouse drivers.

I will try other protocols ("auto-dev" and "exps2"; is there any other protocol for test?) later and tell here if anyone works.

---

### Post by pi/roman on 2011-01-07
Could you revert your configuration to a point where your device is listed as any name in xinput if you have not already, then run the following command.
```
/lib/udev/input_id /class/input/event7
```aahcl, you would use event9 instead of event7.

It should say:
> ID_INPUT=1
ID_INPUT_TOUCHPAD=1but i'm guessing it says
> ID_INPUT=1
ID_INPUT_MOUSE=1

---

### Post by WthIteh on 2011-01-08
> **pi/roman said:**
> Could you revert your configuration to a point where your device is listed as any name in xinput if you have not already, then run the following command.
```
/lib/udev/input_id /class/input/event7
```
Yes, it is so.
Both when *xinput --list* output is
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
```and when *xinput --list* output is
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Touchpad                                    id=6    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
```the */lib/udev/input_id /class/input/event7* command output is:
```
ID_INPUT=1
ID_INPUT_MOUSE=1
```

---

### Post by pi/roman on 2011-01-08
> the */lib/udev/input_id /class/input/event7* command output is:
```
ID_INPUT=1
 ID_INPUT_MOUSE=1
```Excellent.  Well, that's not really a good thing but at least i think we are approaching the root of the problem now. I believe this is where the input id is being mislabeled.

We will need to create a udev rule to change the input id to touchpad.  Once that is done everything should work normally. We may also need to remove the input id of 'mouse' on it but i don't think that is necessary and maybe not possible either. I will work on a rule and test it on my own computer before i recommend it, or if you create a rule to fix it i would be interested in seeing the results. I have to go for now but will try to have a fix within a few days.

---

### Post by pi/roman on 2011-01-08
Ok, i made a very simple udev rule to fix this and i'm almost sure it will work and may just need some slight tweaking.  I successfully did the reverse on my own computer to test it out.

There is a udev rules file to edit, it may be a good idea to create a shortcut to it using this command for quick access:
```
gksudo gedit /lib/udev/rules.d/60-persistent-input.rules
```Here are the contents of the file along with the changes that need to be made marked in red. Just before the line in red, the input id of your touchpad is read by "input_id %p".  It will be read incorrectly as id_input_mouse=1.  The added rule will recognize your touchpad device listed a[COLOR=black]s [/COLOR][COLOR=black]"PS/2 Generic Mouse"[/COLOR] and first add input id touchpad then remove input id mouse.  That's it. Everything else will occur normally and your device will be registered as a touchpad.

```
# do not edit this file, it will be overwritten on update

ACTION=="remove", GOTO="persistent_input_end"
SUBSYSTEM!="input", GOTO="persistent_input_end"
KERNEL=="input[0-9]*", GOTO="persistent_input_end"

ENV{ID_INPUT}=="", IMPORT{program}="input_id %p"
SUBSYSTEMS=="usb", ENV{ID_BUS}=="", IMPORT{program}="usb_id --export %p"

[COLOR=Red]ATTRS{name}=="PS/2 Generic Mouse", ENV{ID_INPUT_TOUCHPAD}="1", ENV{ID_INPUT_MOUSE}=""[/COLOR]

# determine class name for persistent symlinks
ENV{ID_INPUT_KEYBOARD}=="?*", ENV{.INPUT_CLASS}="kbd"
ENV{ID_INPUT_MOUSE}=="?*", ENV{.INPUT_CLASS}="mouse"
ENV{ID_INPUT_TOUCHPAD}=="?*", ENV{.INPUT_CLASS}="mouse"
ENV{ID_INPUT_TABLET}=="?*", ENV{.INPUT_CLASS}="mouse"
ENV{ID_INPUT_JOYSTICK}=="?*", ENV{.INPUT_CLASS}="joystick"
DRIVERS=="pcspkr", ENV{.INPUT_CLASS}="spkr"
ATTRS{name}=="*dvb*|*DVB*|* IR *", ENV{.INPUT_CLASS}="ir"

# fill empty serial number
ENV{.INPUT_CLASS}=="?*", ENV{ID_SERIAL}=="", ENV{ID_SERIAL}="noserial"

# by-id links
KERNEL=="mouse*|js*", ENV{ID_BUS}=="?*", ENV{.INPUT_CLASS}=="?*", SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-$env{.INPUT_CLASS}"
KERNEL=="event*", ENV{ID_BUS}=="?*", ENV{.INPUT_CLASS}=="?*", SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-event-$env{.INPUT_CLASS}"
# allow empty class for USB devices, by appending the interface number
SUBSYSTEMS=="usb", ENV{ID_BUS}=="?*", KERNEL=="event*", ENV{.INPUT_CLASS}=="", ATTRS{bInterfaceNumber}=="?*", \
  SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-event-if$attr{bInterfaceNumber}"

# by-path
SUBSYSTEMS=="pci|usb|platform", IMPORT{program}="path_id %p"
ENV{ID_PATH}=="?*", KERNEL=="mouse*|js*", ENV{.INPUT_CLASS}=="?*", SYMLINK+="input/by-path/$env{ID_PATH}-$env{.INPUT_CLASS}"
ENV{ID_PATH}=="?*", KERNEL=="event*", ENV{.INPUT_CLASS}=="?*", SYMLINK+="input/by-path/$env{ID_PATH}-event-$env{.INPUT_CLASS}"
# allow empty class for platform and usb devices; platform supports only a single interface that way
SUBSYSTEMS=="usb|platform", ENV{ID_PATH}=="?*", KERNEL=="event*", ENV{.INPUT_CLASS}=="", \
  SYMLINK+="input/by-path/$env{ID_PATH}-event"

LABEL="persistent_input_end"
```

---

### Post by WthIteh on 2011-01-09
One step forward :) Thanks.

After reboot mouse was disabled!
But output of xinput --list command changed to:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Touchpad                                    id=6    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```
which is a good step. PS/2 Generic Mouse is removed and Touchpad is detected there.

And here is output of *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* command:
```

[    56.430] (**) |-->Input Device "Touchpad"
[    56.430] (**) |-->Input Device "Mouse"
[    56.430] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    56.430] (WW) Disabling Mouse
[    56.562] (II) LoadModule: "synaptics"
[    56.562] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    56.562] (II) Module synaptics: vendor="X.Org Foundation"
[    56.628] (==) intel(0): Silken mouse enabled
[    56.707] (II) Synaptics touchpad driver version 1.2.2
[    56.707] (**) Option "Device" "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
[    57.034] (**) Option "CorePointer"
[    57.034] (**) Touchpad: always reports core events
[    57.193] (II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
[    57.193] (**) Touchpad: (accel) keeping acceleration scheme 1
[    57.193] (**) Touchpad: (accel) acceleration profile 0
[    57.194] (**) Touchpad: (accel) acceleration factor: 2.000
[    57.194] (**) Touchpad: (accel) acceleration threshold: 4
[    57.691] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    57.691] (**) PS/2 Generic Mouse: Applying InputClass "evdev touchpad catchall"
[    57.691] (**) PS/2 Generic Mouse: Applying InputClass "touchpad catchall"
[    57.691] (II) Synaptics touchpad driver version 1.2.2
[    58.121] (--) PS/2 Generic Mouse: no supported touchpad found
[    58.121] (EE) PS/2 Generic Mouse Unable to query/initialize Synaptics hardware.
[    58.161] (EE) PreInit failed for input device "PS/2 Generic Mouse"
[    58.161] (II) UnloadModule: "synaptics"
[    58.161] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)

```

What is the next step?

---

### Post by pi/roman on 2011-01-09
We made changes to your xorg files which should not be needed now as your touchpad is being loaded properly.  Here is what the original files look like for reference if you have not already reverted them.

/usr/share/X11/xorg.conf.d/10-evdev.conf
> #
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection/usr/share/X11/xorg.conf.d/50-synaptics.conf
> Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
EndSectionThen I would like to get an idea how the functionality of your touchpad is.  Does it operate at all? Does it jump around or fairly normal?
Can you use synclient now?
```
synclient -l
```You should be able to remove the touchpad configuration xorg.conf if you want which would be the identifier in the "serverlayout" section and the entire touchpad inputdevice section.  It's not necessary, but that is what is causing the name "PS/2 Generic Mouse" to be changed to "Touchpad".  If the protocol "alps" option is still there then it is also affecting it in that way.  If you are having problems you may want to try it without that option but I'm not sure as I don't have an alps touchpad.

---

### Post by WthIteh on 2011-01-09
Three experiments:

[LIST=1]
[*]I removed xorg.conf as initial state (at the beginning I had no xorg.conf file)
[LIST]
[*]In this case neither PS/2 nor Touchpad were detected by xinput --list
[*]Mouse was completely disabled
[/LIST]
[*]Then using previous xorg.conf and *Option "Protocol"   "alps"* removed
[LIST]
[*]In this case xinput did not detect neither PS/2 nor Touchpad too
[*]Mouse was disabled completely too
[/LIST]
[*]Then using previous xorg.conf with *Option "Protocol"   "alps"* command.
[LIST]
[*]In this case xinput detect *Touchpad* as posted above.
[*]synclient works too :)
[/LIST]
[/LIST]
In 3rd situation:
I could not control mouse in anyway.
After reboot, I could not move mouse or click/right-click. But if I continue trying to move the mouse, it will move to one of the screen corners (at random) after some seconds and stop there. If I try for some more seconds, it will move to another random corner suddenly. It also do some clicks at random in screen corners.

Here is the output of *synclient -l* command:
```

Parameter settings:
    LeftEdge                = 1900
    RightEdge               = 5400
    TopEdge                 = 1900
    BottomEdge              = 4000
    FingerLow               = 25
    FingerHigh              = 30
    FingerPress             = 256
    MaxTapTime              = 180
    MaxTapMove              = 220
    MaxDoubleTapTime        = 180
    SingleTapTimeout        = 180
    ClickTime               = 100
    FastTaps                = 0
    EmulateMidButtonTime    = 75
    EmulateTwoFingerMinZ    = 257
    EmulateTwoFingerMinW    = 7
    VertScrollDelta         = 100
    HorizScrollDelta        = 100
    VertEdgeScroll          = 1
    HorizEdgeScroll         = 0
    CornerCoasting          = 0
    VertTwoFingerScroll     = 0
    HorizTwoFingerScroll    = 0
    MinSpeed                = 0.4
    MaxSpeed                = 0.7
    AccelFactor             = 0.01
    TrackstickSpeed         = 40
    EdgeMotionMinZ          = 30
    EdgeMotionMaxZ          = 160
    EdgeMotionMinSpeed      = 1
    EdgeMotionMaxSpeed      = 400
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
    PalmMinZ                = 200
    CoastingSpeed           = 0
    PressureMotionMinZ      = 30
    PressureMotionMaxZ      = 160
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

---

### Post by pi/roman on 2011-01-09
Thanks, that is a good explanation. I feel like we almost have it but not exactly sure what needs to be done.  I think we should try to remove the errors from the xorg log. Since the only thing causing the errors look to be the changes we made to xorg.conf and you had nothing in it before, it would be best to erase it and start from scratch. This way we can assign the alps protocol directly to "PS/2 Generic Mouse" without changing it's name.

So open xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```clear it out as long as you didn't have anything in there except for the touchpad configurations that we made.

Then place this in it which will assign the protocol to the class rather than the device and will be cumulative to the class assignments already registered.
```
Section "InputClass"
Identifier "Touchpad"
MatchIsTouchpad "on"
Option "Protocol" "alps"
EndSection
```Then I would like to run a udev test on it. It is a lot of output so you can send it to a file on your desktop and then upload it.  I think it is "input/mouse0" unless you have a mouse plugged in it could be "input/mouse1"
```
udevadm test -a add $(udevadm info -q path -n input/mouse0) 2>~/Desktop/udevtest
```Also the Xorg.0.log would be nice to look at again after this change and I am hoping the errors will be gone.

---

### Post by WthIteh on 2011-01-10
OK, I did two experiments:
**First.** Using following *xorg.conf* file:
```

Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
EndSection

Section "InputClass"
    Identifier    "Touchpad"
    MatchIsTouchpad    "on"
    Option        "Protocol"    "alps"
EndSection

```I'm using vim as my preferred editor. As vim highlights the file, I could conclude that InputClass should not be placed in the xorg.conf file! Am I (vim highlighting) right?
BTW, X could not start with this xorg.conf file.

I changed the xorg.conf in recovery mode for second experiment (I thought bug was from unremoved Touchpad entry in ServerLayout by my mistake while its InputDevice was removed).
**Second.** Using following *xorg.conf* file:
```

Section "InputClass"
    Identifier    "Touchpad"
    MatchIsTouchpad    "on"
    Option        "Protocol"    "alps"
EndSection

```In this case X start normally, but Touchpad was not detected by xinput.
This is output of *xinput --list* command:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]

```I did not test the xorg.conf with both InputDevice and InputClass simultaneously since I thought InputClass should cover InputDevice effects. Should I test them simultaneously too?

Here is output of *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* command:
```

[    54.072] (==) intel(0): Silken mouse enabled
[    54.461] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    54.461] (**) PS/2 Generic Mouse: Applying InputClass "evdev touchpad catchall"
[    54.461] (**) PS/2 Generic Mouse: Applying InputClass "touchpad catchall"
[    54.461] (**) PS/2 Generic Mouse: Applying InputClass "Touchpad"
[    54.461] (II) LoadModule: "synaptics"
[    54.462] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    54.462] (II) Module synaptics: vendor="X.Org Foundation"
[    54.462] (II) Synaptics touchpad driver version 1.2.2
[    55.051] (--) PS/2 Generic Mouse: no supported touchpad found
[    55.051] (EE) PS/2 Generic Mouse Unable to query/initialize Synaptics hardware.
[    55.171] (EE) PreInit failed for input device "PS/2 Generic Mouse"
[    55.171] (II) UnloadModule: "synaptics"
[    55.171] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[    55.171] (**) PS/2 Generic Mouse: Applying InputClass "Touchpad"

```And output of
```

udevadm test -a add $(udevadm info -q path -n input/mouse0) 2>~/Desktop/udevtest

```(in the second experiment) is attached.

---

### Post by pi/roman on 2011-01-10
You don't need to have a serverlayout with an input class, it is only to  name the configured devices. InputClass is ok to use in xorg.conf  but Vim probably just does not recognise them.

The udev test looks normal so i don't think it will show where the problem is.  There is more udev info to look at but as of now i think it is a priority to get your device listed in xinput again. I was hoping the auto detections would take care of it after we removed the custom configurations but that doesn't seem to be the case. Looking back through the topic it looks as though we came closest to it in your 3rd experiment of post #46. So That would have been with your xorg.conf that looked something like this:
```
Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Protocol"    "alps"
    Option        "Device"    "/dev/input/event7"
EndSection
```Something we didn't do that would be good is take a look a the X properties of the device once it is listed. So if it is detected as Touchpad then:
```
xinput list-props Touchpad
```

---

### Post by pi/roman on 2011-01-10
double post

---

### Post by pi/roman on 2011-01-10
forum server connection fail

---

### Post by pi/roman on 2011-01-10
forum server connection fail

---

### Post by pi/roman on 2011-01-10
forum server connection fail

---

### Post by WthIteh on 2011-01-10
Using following xorg.conf file:
```

Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Protocol"    "alps"
    Option        "Device"    "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
    Option        "UpDownScrolling"    "1"
EndSection

Section "InputClass"
    Identifier    "Touchpad"
    MatchIsTouchpad    "on"
    Option        "Protocol"    "alps"
EndSection

```
This is the output of xinput --list-props for Touchpad device:
```

Device 'Touchpad':
    Device Enabled (125):    1
    Coordinate Transformation Matrix (127):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (242):    0
    Device Accel Constant Deceleration (243):    1.000000
    Device Accel Adaptive Deceleration (244):    1.000000
    Device Accel Velocity Scaling (245):    10.000000
    Synaptics Edges (246):    1900, 5400, 1900, 4000
    Synaptics Finger (247):    25, 30, 256
    Synaptics Tap Time (248):    180
    Synaptics Tap Move (249):    220
    Synaptics Tap Durations (250):    180, 180, 100
    Synaptics Tap FastTap (251):    0
    Synaptics Middle Button Timeout (252):    75
    Synaptics Two-Finger Pressure (253):    257
    Synaptics Two-Finger Width (254):    7
    Synaptics Scrolling Distance (255):    100, 100
    Synaptics Edge Scrolling (256):    1, 0, 0
    Synaptics Two-Finger Scrolling (257):    0, 0
    Synaptics Move Speed (258):    0.400000, 0.700000, 0.010000, 40.000000
    Synaptics Edge Motion Pressure (259):    30, 160
    Synaptics Edge Motion Speed (260):    1, 400
    Synaptics Edge Motion Always (261):    0
    Synaptics Button Scrolling (262):    1, 1
    Synaptics Button Scrolling Repeat (263):    1, 1
    Synaptics Button Scrolling Time (264):    100
    Synaptics Off (265):    0
    Synaptics Guestmouse Off (266):    0
    Synaptics Locked Drags (267):    0
    Synaptics Locked Drags Timeout (268):    5000
    Synaptics Tap Action (269):    2, 3, 0, 0, 1, 3, 2
    Synaptics Click Action (270):    1, 3, 2
    Synaptics Circular Scrolling (271):    0
    Synaptics Circular Scrolling Distance (272):    0.100000
    Synaptics Circular Scrolling Trigger (273):    0
    Synaptics Circular Pad (274):    0
    Synaptics Palm Detection (275):    0
    Synaptics Palm Dimensions (276):    10, 200
    Synaptics Coasting Speed (277):    0.000000
    Synaptics Pressure Motion (278):    30, 160
    Synaptics Pressure Motion Factor (279):    1.000000, 1.000000
    Synaptics Grab Event Device (280):    1
    Synaptics Gestures (281):    1
    Synaptics Capabilities (282):    0, 0, 0, 0, 0
    Synaptics Pad Resolution (283):    1, 1
    Synaptics Area (284):    0, 0, 0, 0
    Synaptics Jumpy Cursor Threshold (285):    0

```
And when PS/2 Generic Mouse (not the Touchpad) is detected, this is xinput --list-props output for the PS/2 generic Mouse device:
```

Device 'PS/2 Generic Mouse':
    Device Enabled (125):    1
    Coordinate Transformation Matrix (127):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (244):    0
    Device Accel Constant Deceleration (245):    1.000000
    Device Accel Adaptive Deceleration (246):    1.000000
    Device Accel Velocity Scaling (247):    10.000000
    Evdev Reopen Attempts (242):    10
    Evdev Axis Inversion (248):    0, 0
    Evdev Axes Swap (250):    0
    Axis Labels (251):    "Rel X" (135), "Rel Y" (136)
    Button Labels (252):    "Button Left" (128), "Button Middle" (129), "Button Right" (130), "Button Wheel Up" (131), "Button Wheel Down" (132)
    Evdev Middle Button Emulation (253):    2
    Evdev Middle Button Timeout (254):    50
    Evdev Wheel Emulation (255):    0
    Evdev Wheel Emulation Axes (256):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (257):    10
    Evdev Wheel Emulation Timeout (258):    200
    Evdev Wheel Emulation Button (259):    4
    Evdev Drag Lock Buttons (260):    0

```

Also if I use
```

    Option        "Device"    "/dev/input/event7"

```
instead of
```

    Option        "Device"    "/dev/input/by-path/platform-i8042-serio-4-event-mouse"

```
in the xorg.conf file, X will not start! which is strange since /dev/input/by-path/platform-i8042-serio-4-event-mouse is a symbolic link to /dev/input/event7 itself!

---

### Post by pi/roman on 2011-01-10
This is interesting here:
> **WthIteh said:**
> 
    Synaptics Capabilities (282):    0, 0, 0, 0, 0

Then from the synaptics manual:
>        Synaptics Capabilities
              This read-only property expresses the  physical  capability  of  the  touchpad,  most
              notably whether the touchpad hardware supports multi-finger tapping and scrolling.

              8  bit  (BOOL),  5  values (read-only), has left button, has middle button, has right
              button, two-finger detection, three-finger detection.
My touchpad has every capabilty except the middle button. This is a read only property so that would mean that the kernel has to apply it.
also
> NOTES
       If  either of Protocol "auto-dev" (default) or Protocol "event" is used, the driver initial&#8208;
       izes defaults based on the capabilities reported by the kernel driver.  Acceleration,  edges
       and  resolution  are  based  on the dimensions reported by the kernel. If the kernel reports
       multi-finger detection, two-finger vertical  scrolling  is  enabled,  horizontal  two-finger
       scrolling  is  disabled  and edge scrolling is disabled. If no multi-finger capabilities are
       reported, edge scrolling is enabled for both horizontal and vertical scrolling.  Tapping  is
       disabled  by default for touchpads with one or more physical buttons.  To enable it you need
       to map tap actions to buttons. See the "TapButton1", "TapButton2" and "TapButton3" options.

       Button mapping for physical buttons is handled in the server.  If the device is switched  to
       left-handed  (an  in-server mapping of physical buttons 1, 2, 3 to the logical buttons 3, 2,
       1, respectively), both physical and TapButtons are affected. To counteract this, the TapBut&#8208;
       tons need to be set up in reverse order (TapButton1=3, TapButton2=1).You tried the auto-dev protocol earlier and it didn't work, maybe try the event protocol.

It's strange that the device event didn't work but good call to find another method. It probably changed and you could look it up in hwinfo --mouse to see what it is now.

---

### Post by WthIteh on 2011-01-10
> **pi/roman said:**
> 
You tried the auto-dev protocol earlier and it didn't work, maybe try the event protocol.

It's strange that the device event didn't work but good call to find another method. It probably changed and you could look it up in hwinfo --mouse to see what it is now.
I tried "auto", "auto-dev", "event", "alps", and "xlps" protocols but only
```

    Option        "Protocol"    "alps"

```
could cause *xinput* to detect the Touchpad.

And there is no change in output of hwinfo --mouse as I could see:
```

> hal.1: read hal dataprocess 2432: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
36: PS/2 00.0: 10500 PS/2 Mouse                                 
  [Created at input.183]
  Unique ID: AH6Q.U5GX9Ignjc0
  Hardware Class: mouse
  Model: "PS/2 Generic Mouse"
  Vendor: 0x0002 
  Device: 0x0001 "PS/2 Generic Mouse"
  Compatible to: int 0x0210 0x0003
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event7, /dev/char/13:71, /dev/input/by-path/platform-i8042-serio-4-event-mouse, /dev/char/13:32, /dev/input/by-path/platform-i8042-serio-4-mouse, /dev/char/13:63
  Device Number: char 13:63 (char 13:32)
  Driver Info #0:
    Buttons: 3
    Wheels: 0
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

---

### Post by pi/roman on 2011-01-10
You can comment out the inputclass section so you don't have to worry about changing the protocol in both sections if you want to try a different one.  It seems like the inputdevice section is needed for now though anyway  to make it recognized.

I have some more things to try to get it working.

First thing to do is remove the synaptics driver package:
```
sudo apt-get remove --purge xserver-xorg-input-synaptics
```Then run an update:
```
sudo apt-get update && sudo apt-get upgrade
```Then reboot your computer and see if your touchpad is picked up by the mouse driver. The goal is not to run it off the mouse driver but to see if it will at least be picked up by it as it was before. If it is not operable try some of these commands:
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=exps
``````
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
``````
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=any
```If it is operable, it should work about the same as it did before.
Then reinstall the synaptics driver:
```
sudo apt-get install xserver-xorg-input-synaptics
```Then reboot the computer again and see if the touchpad is operable. If not, then modprobe the driver again with proto=imps or proto=exps which are the mouse drivers. Use proto=any to try to get it to take the synaptics driver.
If your touchpad is still not operable then install gpointing device settings:
```
 sudo apt-get install gpointing-device-settings
```Check in the settings there to see if your touchpad will show up.

---

### Post by WthIteh on 2011-01-11
Good and Bad News.....

First I removed driver and update by
```

sudo apt-get remove --purge xserver-xorg-input-synaptics
sudo apt-get update && sudo apt-get upgrade

```While xorg.conf content was as:
```


Section "ServerLayout"
    Identifier    "Default Layout"
    InputDevice    "Touchpad"    "CorePointer"
EndSection

Section "InputDevice"
    Identifier    "Touchpad"
    Driver        "synaptics"
    Option        "Protocol"    "alps"
    Option        "Device"    "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
    Option        "UpDownScrolling"    "1"
EndSection

```After reboot, touchpad was operable completely (else of vertical scrolling) and was detected by *xinput --list* as PS/2 Generic Mouse device.
Here is output of *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* at that point:
```

[    54.729] (**) |-->Input Device "Touchpad"
[    54.765] (II) LoadModule: "synaptics"
[    54.766] (WW) Warning, couldn't open module synaptics
[    54.766] (II) UnloadModule: "synaptics"
[    54.766] (EE) Failed to load module "synaptics" (module does not exist, 0)
[    54.831] (==) intel(0): Silken mouse enabled
[    54.919] (II) LoadModule: "synaptics"
[    54.919] (WW) Warning, couldn't open module synaptics
[    54.919] (II) UnloadModule: "synaptics"
[    54.919] (EE) Failed to load module "synaptics" (module does not exist, 0)
[    54.919] (EE) No input driver matching `synaptics'
[    55.361] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    55.361] (**) PS/2 Generic Mouse: Applying InputClass "evdev touchpad catchall"
[    55.361] (**) PS/2 Generic Mouse: always reports core events
[    55.361] (**) PS/2 Generic Mouse: Device: "/dev/input/event7"
[    55.441] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    55.441] (II) PS/2 Generic Mouse: Found relative axes
[    55.441] (II) PS/2 Generic Mouse: Found x and y relative axes
[    55.441] (II) PS/2 Generic Mouse: Configuring as mouse
[    55.441] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    55.441] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    55.441] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    55.441] (II) PS/2 Generic Mouse: initialized for relative axes.
[    55.441] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)

```Then I installed driver by
```
sudo apt-get install xserver-xorg-input-synaptics
```and after reboot, touchpad was NOT operable, but detected by *xinput --list* as Touchpad device.
So I try followings respectively to make it operable:
```

sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=exps
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=any

```
But neither of three above protocols could not make touchpad operable.
Here is output of *cat /var/log/Xorg.0.log | grep -iE 'mouse|touchpad|pointer|synaptics'* at that point:
```

[    55.515] (**) |-->Input Device "Touchpad"
[    55.604] (II) LoadModule: "synaptics"
[    55.604] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    55.604] (II) Module synaptics: vendor="X.Org Foundation"
[    55.670] (==) intel(0): Silken mouse enabled
[    55.749] (II) Synaptics touchpad driver version 1.2.2
[    55.749] (**) Option "Device" "/dev/input/by-path/platform-i8042-serio-4-event-mouse"
[    56.054] (**) Option "CorePointer"
[    56.054] (**) Touchpad: always reports core events
[    56.153] (II) XINPUT: Adding extended input device "Touchpad" (type: TOUCHPAD)
[    56.153] (**) Touchpad: (accel) keeping acceleration scheme 1
[    56.153] (**) Touchpad: (accel) acceleration profile 0
[    56.153] (**) Touchpad: (accel) acceleration factor: 2.000
[    56.153] (**) Touchpad: (accel) acceleration threshold: 4
[    56.791] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event7)
[    56.791] (**) PS/2 Generic Mouse: Applying InputClass "evdev touchpad catchall"
[    56.791] (**) PS/2 Generic Mouse: Applying InputClass "touchpad catchall"
[    56.791] (II) Synaptics touchpad driver version 1.2.2
[    57.101] (--) PS/2 Generic Mouse: no supported touchpad found
[    57.101] (EE) PS/2 Generic Mouse Unable to query/initialize Synaptics hardware.
[    57.181] (EE) PreInit failed for input device "PS/2 Generic Mouse"
[    57.181] (II) UnloadModule: "synaptics"
[    57.181] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)

```
So I installed  gpointing-device-settings by:
```
sudo apt-get install gpointing-device-settings
```
and then running it by
```
gpointing-device-settings
```
Interesting :) There was Touchpad and one checkbox saying "Disable touchpad".
I removed that checkmark.
But touchpad was not operable yet. I try one reboot. After reboot checkmark was not there as expected (touchpad should be enabled) but it was not operable yet.

So I revert settings by commenting changes in config files and after reboot I reach previous PS/2 Generic Mouse device. This time running
```
gpointing-device-settings
```shows two settings for PS/2 Generic Mouse for emulating middle mouse button and another for Wheel emulation (which was what I missed in my touchpad). If it works too, I reach my required functionality. So I enabled it. It wants button 1 or 2 or 3 or 4 for mouse wheel emulation. Using button 1, I could vertical / horizontal scroll by mouse click and move. But in this way I could not tap-and-drag anymore. By button 2, I could not make scrolling to work. With button 3, it does tap-and-drag and scrolling and selection simultaneously which is somehow terrible. With button 4, I could not make scrolling to work again.

What should I do now?

---

### Post by pi/roman on 2011-01-12
I don't believe you will have enough buttons under the mouse driver to have all those options.  You could try to run "xinput test" on your device and  see how many buttons you can get to register.  Try motioning along the edge to get a scroll button or tapping to generate a button click.

There is an old topic here [[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=417492&page=5[/COLOR]]("http://ubuntuforums.org/showthread.php?t=417492&page=5") that recommends using boot parameters and it looks like many have had success with them. I tested them myself to make sure they won't blow up the computer but I don't have any problems to fix with them.  You could try i8042=reset i8042=nomux and i8042=nopnp in your grub.cfg.
```
sudo gedit /boot/grub/grub.cfg
```Below this line > ### BEGIN /etc/grub.d/10_linux ### is your first menu entry.

In this menu entry at the end of this line>       linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e411621d-c5a8-4ba9-bb66-65ec1f8fa0ec ro  place a space then the boot parameters.

I would also like to see the udev attributes:
```
udevadm info -a -n char/13:32
```

---

### Post by WthIteh on 2011-01-12
I followed the instructions for boot commands (from [http://ubuntuforums.org/showthread.php?t=417492&page=5](http://ubuntuforums.org/showthread.php?t=417492&page=5)), but it made no difference.
However tpconfig could recognize my touchpad as was said there.
This is output of *sudo tpconfig -i* command:
```

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;        no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```And here is the output of  *udevadm info -a -n char/13:32* command:
```


Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/platform/i8042/serio4/input/input7/mouse0':
    KERNEL=="mouse0"
    SUBSYSTEM=="input"
    DRIVER==""

  looking at parent device '/devices/platform/i8042/serio4/input/input7':
    KERNELS=="input7"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{name}=="PS/2 Generic Mouse"
    ATTRS{phys}=="isa0060/serio4/input0"
    ATTRS{uniq}==""
    ATTRS{modalias}=="input:b0011v0002p0001e0000-e0,1,2,k110,111,112,r0,1,amlsfw"

  looking at parent device '/devices/platform/i8042/serio4':
    KERNELS=="serio4"
    SUBSYSTEMS=="serio"
    DRIVERS=="psmouse"
    ATTRS{description}=="i8042 AUX3 port"
    ATTRS{modalias}=="serio:ty01pr00id00ex00"
    ATTRS{bind_mode}=="auto"
    ATTRS{protocol}=="PS/2"
    ATTRS{rate}=="100"
    ATTRS{resolution}=="200"
    ATTRS{resetafter}=="5"
    ATTRS{resync_time}=="0"

  looking at parent device '/devices/platform/i8042':
    KERNELS=="i8042"
    SUBSYSTEMS=="platform"
    DRIVERS=="i8042"
    ATTRS{modalias}=="platform:i8042"

  looking at parent device '/devices/platform':
    KERNELS=="platform"
    SUBSYSTEMS==""
    DRIVERS==""

```

I also checked *xinput test 12* (12 is id of PS/2 in xinput list output) while my touchpad was detected as PS/2 Generic Mouse and it shows "movement", "button 1 for left click", "button 2 for emulated middle click" and "button 3 for right click" but nothing special for edge scrolling or edge tapping or tapping, etc.

---

### Post by WthIteh on 2011-01-12
Duplicate post

---

### Post by WthIteh on 2011-01-12
Duplicate post

---

### Post by pi/roman on 2011-01-12
I believe in order to have edge scrolling and regular buttons too your touchpad would need to have hardware driven scrolling and maybe yours does not so then it would be necessary to load the touchpad driver to make it work.  It looks to me like the only way to get touchpad driver loaded would be to apply a patch although I hope I am wrong and someone can give some advice on it.

If you do decide to patch your driver you would need to get the debug data from your touchpad.  You can do so by applying the "i8042.debug" parameter to the boot options as you did previously. Then as soon as the computer boots up. Save the dmesg log to a file.
```
dmesg > ~/Desktop/i8042boot.log
```If you wait too long you may lose some important data regarding the initialization of the touchpad so try not to use the touchpad too much before saving the log.

Then you can report the bug on Launchpad and include the logged data along with other important information like lspci and you may not receive a lot of help there so you should probably also start a new forum topic asking for help in identifying your touchpad signature and applying it to a driver patch.

---

### Post by WthIteh on 2011-01-13
Many thanks for your helps.

My touchpad should support edge scrolling directly because I could see a physically separated area for edge scrolling on my touchpad. Below is an ascii-art picture of my touchpad :)
[HTML]
...............................
...........................  ..
...........................  ..
...........................  ..
...........................  ..
...........................  ..
...............................
...............................
[/HTML]I also do not want to patch my driver. Instead I will wait for an official update. I want to keep my system standard!

---

### Post by pi/roman on 2011-01-13
If you want to get vertical scrolling without patching the driver, i believe the goal here will be to force it to take the "imps" protocol which allows for scrolling data. If there is any way to do it then maybe it will be to use the input controller boot parameters ( i8042=reset i8042=nomux i8042=nopnp) either a single one or combination, then modprobe the driver using "imps" protocol:
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
```

---

### Post by vickychijwani on 2011-01-25
> **pi/roman said:**
> You can comment out the inputclass section so you don't have to worry about changing the protocol in both sections if you want to try a different one.  It seems like the inputdevice section is needed for now though anyway  to make it recognized.

I have some more things to try to get it working.

First thing to do is remove the synaptics driver package:
```
sudo apt-get remove --purge xserver-xorg-input-synaptics
```Then run an update:
```
sudo apt-get update && sudo apt-get upgrade
```Then reboot your computer and see if your touchpad is picked up by the mouse driver. The goal is not to run it off the mouse driver but to see if it will at least be picked up by it as it was before. If it is not operable try some of these commands:
```
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=exps
``````
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=imps
``````
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=any
```If it is operable, it should work about the same as it did before.
Then reinstall the synaptics driver:
```
sudo apt-get install xserver-xorg-input-synaptics
```Then reboot the computer again and see if the touchpad is operable. If not, then modprobe the driver again with proto=imps or proto=exps which are the mouse drivers. Use proto=any to try to get it to take the synaptics driver.
If your touchpad is still not operable then install gpointing device settings:
```
 sudo apt-get install gpointing-device-settings
```Check in the settings there to see if your touchpad will show up.

Thanks buddy! The "proto=any" command solved my scrolling problem! :D

---

### Post by bridgeco on 2011-02-12
Just to take pi/roman's and vickychijwani's posts a little further:

I was having this problem on an Acer 7551G notebook; I did the following to load psmouse with proto=imps automatically.  
Note: The first line will disable your mouse so make sure you're ready to type!

```

sudo apt-get remove xserver-xorg-input-synaptics

```

Create a file named **psmouse.conf** in** /etc/modprobe.d**
```
touch /etc/modprobe.d/psmouse.conf
nano /etc/modprobe.d/psmouse.conf

```

paste this onto the 1st line:

```
options psmouse proto=imps
```

You can test the .conf syntax with 'modprobe -v psmouse' if you'd like.
Reboot.



This ain't going to enable multitouch and other fanciness but scrollbar will work like it should.

---

### Post by juanfpina on 2011-02-13
No matter what proto=whatever I use, I never get the scrolling. I was able to get it to detect my touchpad as a touchpad, but as previously stated the mouse would go crazy. Anything else I can try? I tried everything in the thread, I have an alps touchpad.

---

### Post by samba123 on 2011-10-21
sudo modprobe -rv psmouse
sudo modprobe -v psmouse proto=**any**

worked for me :)

---

### Post by Denver Dave on 2011-11-22
I have a windows 7, Acer Aspire 7741Z laptop running ubuntu 11.04 and 11.10 from USB sticks.

The vertical scroll bar on the touchpad does not work in either version.  I've tried the commands in the immediately previous post and didn't seem to work.

The cursor does seem to jump around more while running ubuntu than windows 7.

Have tried with boot DVDs with AV Linux 5.0 and also Knoppix 6.7.  The touchpad vertical scroll works with both.   I believe that the cursor jumping around is also somewhat better, but this is subjective.  The vertical scroll definitely works.

Hope this information helps.
= = = = = = 

Found this which added vertical scroll to my touch pad.  Amazing worked after all the configuration and term commands I tried:
[https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty](https://help.ubuntu.com/community/Laptop/Sony/Vaio/FSeries/Natty)

> Keyboard and Touchpad

Basic features of the keyboard and touchpad work out of the box. However, the scroll function does not work out of the box at most recent check. If you have this problem, it is possible to fix using the following command:

echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse

This will tell Linux to treat the touchpad as a generic PS/2 mouse with a scroll wheel. Scrolling on the right-hand side of the touchpad should now work. However, horizontal scrolling does not work. 

Let me double check, before I post - yes touchpad vertical scroll working.

The approach above to add vertical scroll removes the touchpad tab from the mouse properties.  Worth the trade for me, but does seem like a "bug" work-around.

---

