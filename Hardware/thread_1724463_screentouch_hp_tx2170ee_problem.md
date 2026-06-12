---
title: "screentouch hp tx2170ee problem"
date: 2011-04-08
forum: Hardware
---

### Post by i.s.s.w on 2011-04-08
hi Guys

i have problem on screen touch in my laptop after i install ubuntu 10-10

when i touch the secreen, the mouse move to the left corner of the screen directly

how can fixed this problem 

i am new to the ubuntu 

search from google   i see all posted but error on my system

now i reinstall my ubuntu and more problems happened 

xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController             id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]

---

### Post by Favux on 2011-04-08
Hi i.s.s.w,

Welcome to Ubuntu forums!

The output from *xinput list* indicates:
> &#9116; &#8627; eGalax INC. USB TouchController id=11 [slave pointer (2)]
So you have an eGalax touchscreen.  And have something to search with.

Because you see the touch screen in xinput list the usb kernel driver for eGalax looks like it it working.
> when i touch the secreen, the mouse move to the left corner of the screen directly
When the pointer arrow does that it usually indicates there is a problem with the X driver.

Doing a quick search I found a different netbook with an eGalax:  [http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/11/howto-ubuntu-1010-on-gigabyte-touchnote.html)  linked from:  [http://ubuntuforums.org/showthread.php?t=1613000](http://ubuntuforums.org/showthread.php?t=1613000)  It looks like the eGalax can use the evdev X driver.  That should already be installed.  So all you may need to do is set up a .conf file that matches your tablet and places it on the evdev driver.  As you can see from the Ubuntu thread there may be a little more to it.  And I would handle the .conf file differently than the blog has it.

You should search some more to see if there are instructions specific for your netbook before we go ahead and try that.  I know eGalax has released linux drivers in the past.

---

### Post by i.s.s.w on 2011-04-10
Favux

thanks for help

its working nice but   my muse on touch screen its slow and right click problem

---

### Post by Favux on 2011-04-10
Good, glad you got it working!

> but my muse on touch screen its slow
Are you talking about the pointer arrow for touch or for the SynPS/2 Synaptics TouchPad?
> right click problem 
What's the problem with right click?  And that's for the touchscreen correct?

Let's look at the output of:
```
xinput list-props "eGalax INC. USB TouchController"
```

---

### Post by i.s.s.w on 2011-04-15
after enter 
 	Code:
 	xinput list-props "eGalax INC. USB TouchController" 


root@HP-Pavilion-tx1000-Notebook-PC:~$ xinput list-props "eGalax INC. USB TouchController"
Warning: There are multiple devices matching 'eGalax INC. USB TouchController'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device eGalax INC. USB TouchController
root@HP-Pavilion-tx1000-Notebook-PC:~$

---

### Post by Favux on 2011-04-15
Hi i.s.s.w,

I probably used the wrong "device name" ("eGalax INC. USB TouchController") because it was from the *xinput list* output before you installed the driver.  So repeat:
```
xinput list
```
and then use the correct "device name" in quotes or device ID # in the command.
```
xinput list-props "device name"
```

---

### Post by i.s.s.w on 2011-04-15
than x for help my friend
-----------------------------------

root@HP-Pavilion-tx1000-Notebook-PC:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; egalax                                      id=6    [slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController             id=12    [slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController             id=13    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=16    [slave  keyboard (3)]
root@HP-Pavilion-tx1000-Notebook-PC:~$ xinput list-props "eGalax INC. USB TouchController"
Warning: There are multiple devices matching 'eGalax INC. USB TouchController'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device eGalax INC. USB TouchController

root@HP-Pavilion-tx1000-Notebook-PC:~$ xinput list-props "egalax"
Device 'egalax':
    Device Enabled (117):    1
    Coordinate Transformation Matrix (119):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (235):    0
    Device Accel Constant Deceleration (236):    1.000000
    Device Accel Adaptive Deceleration (237):    1.000000
    Device Accel Velocity Scaling (238):    10.000000

---

### Post by Favux on 2011-04-16
Yup, the *xinput list* changed and you found the touchscreen.  Not much to work with in list-props from what I see.  So what driver did you put it on?  The eGalax one instead of evdev?  What does your .conf file for it look like and what location for it did you use?

Another thing we could look at is your Xorg.0.log in /var/log.

---

### Post by i.s.s.w on 2011-04-17
thank you very much for help me

i am attach my log file

---

### Post by Favux on 2011-04-17
I can't make too much sense out of the Xorg.0.log:
> [    19.310] (II) LoadModule: "egalax"
[    19.310] (II) Loading /usr/lib/xorg/modules/input/egalax_drv.so
[    19.310] (II) Module egalax: vendor="X.Org Foundation"
[    19.310] 	compiled for 1.9.0, module version = 3.5.0
[    19.310] 	Module class: X.Org XInput Driver
[    19.310] 	ABI class: X.Org XInput driver, version 11.0
.........
[    21.072] (**) egalax: always reports core events
[    21.072] (**) egalax X device name: egalax
[    21.072] (II) HID Touch Controller @ /dev/hidraw0 
[    21.072] (**) egalaxHistroSize=10
[    21.072] (**) Option "ScreenNo" "0"
[    21.072] (**) egalax associated screen: 0
[    21.072] (**) egalaxParameter=/var/lib/eeti.param
[    21.072] (**) egalax:Use Defualt Sound Device:/dev/audio
[    21.072] (**) Option "SkipClick" "0"
[    21.072] (**) egalax Rotation option is enabled.
[    21.072] (II) XINPUT: Adding extended input device "egalax" (type: egalax)
..........
[    21.157] (II) config/udev: Adding input device eGalax INC. USB TouchController (/dev/input/event5)
[    21.157] (**) eGalax INC. USB TouchController: Applying InputClass "evdev pointer catchall"
[    21.157] (**) eGalax INC. USB TouchController: always reports core events
[    21.157] (**) eGalax INC. USB TouchController: Device: "/dev/input/event5"
[    21.168] (II) eGalax INC. USB TouchController: Found 3 mouse buttons
[    21.168] (II) eGalax INC. USB TouchController: Found absolute axes
[    21.168] (II) evdev-grail: failed to open grail, no gesture support
[    21.168] (II) eGalax INC. USB TouchController: Found x and y absolute axes
[    21.168] (II) eGalax INC. USB TouchController: Configuring as mouse
[    21.168] (**) eGalax INC. USB TouchController: YAxisMapping: buttons 4 and 5
[    21.168] (**) eGalax INC. USB TouchController: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.168] (II) XINPUT: Adding extended input device "eGalax INC. USB TouchController" (type: MOUSE)
[    21.168] (II) eGalax INC. USB TouchController: initialized for absolute axes.
[    21.168] (II) config/udev: Adding input device eGalax INC. USB TouchController (/dev/input/js0)
[    21.168] (II) No input driver/identifier specified (ignoring)
[    21.168] (II) config/udev: Adding input device eGalax INC. USB TouchController (/dev/input/mouse0)
[    21.169] (II) No input driver/identifier specified (ignoring)
[    21.169] (II) config/udev: Adding input device eGalax INC. USB TouchController (/dev/input/event6)
[    21.169] (**) eGalax INC. USB TouchController: Applying InputClass "evdev tablet catchall"
[    21.169] (**) eGalax INC. USB TouchController: always reports core events
[    21.169] (**) eGalax INC. USB TouchController: Device: "/dev/input/event6"
[    21.180] (II) eGalax INC. USB TouchController: Found absolute axes
[    21.180] (II) evdev-grail: failed to open grail, no gesture support
[    21.180] (II) eGalax INC. USB TouchController: Found x and y absolute axes
[    21.180] (II) eGalax INC. USB TouchController: Found absolute tablet.
[    21.180] (II) eGalax INC. USB TouchController: Configuring as tablet
[    21.180] (**) eGalax INC. USB TouchController: YAxisMapping: buttons 4 and 5
[    21.180] (**) eGalax INC. USB TouchController: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.180] (II) XINPUT: Adding extended input device "eGalax INC. USB TouchController" (type: TABLET)
[    21.180] (II) eGalax INC. USB TouchController: initialized for absolute axes.
[    21.180] (II) config/udev: Adding input device eGalax INC. USB TouchController (/dev/input/mouse1)
[    21.180] (II) No input driver/identifier specified (ignoring)
It's looking like both the eGalax driver and the evdev driver are claiming the tablet.  If true that is a problem.

Since I don't really know what you have done it is hard to help.

This grabs my attention:
> [    21.072] (**) Option "SkipClick" "0"
It does make me wonder what:
```
Option "SkipClick" "1"
```
would do.  But you still haven't described what the right click problem is.

In Maverick (10.10) the configuration files are called .conf files and are located in the xorg.conf.d directory (/usr/share/X11/xorg.conf.d).  So unless you are using the xorg.conf file there should be an eGalax.conf file in the xorg.conf.d.  Also there would be the 05-evdev.conf file.  Two of it's snippets *"evdev pointer catchall"* and *"evdev tablet catchall"*, as I mentioned, also seem to be matching to your touchscreen.  Did you do the blacklisting they talk about in the eGalax install instructions?

---

### Post by i.s.s.w on 2011-04-29
its nice after upgrade to ubontu 11

thank my friend for help me

---

### Post by Favux on 2011-04-29
Great i.s.s.w!  I am glad that Natty Narwhal works for your tablet.

---

