---
title: "Huion 580 Graphics tablet not working"
date: 2013-03-27
forum: Hardware
---

### Post by DaveHockley on 2013-03-27
Hi all,

I originally posted this in the absolute beginners section, but it occourred to me it was totally in the wrong place, sorry about that... I'm still finding my way around here!

On to the post!

I have a Huion 580 graphics tablet (a chinese model). which simply refuses to work on my machine running Ubuntu 12.04.
It sees it, but I can't move the cursor. It will, however, click when I  tap the tablet with the stylus (as it is supposed to do) but the cursor  remains exactly where I left it from when I switch from my mouse.

I have seen other threads regarding the larger model (Huion 610, I  think), but I can't quite follow all the code and things being a bit of a  noob when it comes to the terminal.
I got the model number of 256c:006e from the lsusb command.

Any help on this would be greatly appreciated!

---

### Post by Favux on 2013-03-27
Hi Dave,

Welcome to Ubuntu forums!


The first hurdle, since I assume the tablet is a usb device, is that there needs to be a kernel driver that works for it.  So linking to the other Huion tablet threads might be useful.  Especially since you imply that they got those models working.

Once there is a working kernel driver then the tablet needs an X driver.  The X driver tells the X Server what to draw.  And the X Server is what actually draws the stuff on your monitor.  The X driver would likely be the evdev driver, which is the catch all driver in linux.

Of course there could be a specifically written driver for Huion tablets that may have both the kernel and X driver as part of the package.  Something to keep in mind.

To start diagnostics open a terminal.  With the tablet plugged in enter the following commands in the terminal and post the outputs.
```
lsusb

and

xinput list
```

---

### Post by DaveHockley on 2013-03-28
Hi Favux, Thanks for the reply.

Listed below are the results of the two commands you gave me.


```
dave@raven:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0db0:6877 Micro Star International RT2573
Bus 002 Device 002: ID 256c:006e  
Bus 002 Device 003: ID 062a:6750 Creative Labs 
dave@raven:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HV Huion                                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; HV Huion                                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; HV Huion                                    id=12    [slave  pointer  (2)]
&#9116;   &#8627; MOSART Semi. 2.4G Full-speed Mouse          id=13    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                   id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]
dave@raven:~$ 
```


-Dave

---

### Post by Favux on 2013-03-28
OK, you are basically good to go because mladenkovacevic already showed you can use the WizardPen driver for your tablet if you need to:  [http://ubuntuforums.org/showthread.php?t=2105398](http://ubuntuforums.org/showthread.php?t=2105398)

Apparently the tablet is identified by the line in the lsusb output:
```
Bus 002 Device 002: ID 256c:006e
```
Which would make:
Huion Vendor ID = 256c
tablet Product ID = 006e

It bothers me a little that whatever the Huion has for it in the kernel doesn't even give a name for it in lsusb.  Makes me sort of think we're just seeing the generic HID device code in the kernel and nothing specific for the tablet.

Presumably the tablet is on the evdev driver.  We can determine that by either looking in Xorg.0.log in /var/log or by running the following command in a terminal:
```
xinput list-props ID#
```
Where ID# would come from the **xinput list** output:
```
&#9116;   &#8627; HV Huion                                    id=10    [slave  pointer  (2)]
&#9116;   &#8627; HV Huion                                    id=11    [slave  pointer  (2)]
&#9116;   &#8627; HV Huion                                    id=12    [slave  pointer  (2)]
```
Hopefully the pen is the first entry or ID# 10.  Go ahead and post those outputs.

If it is on the evdev driver it might be evdev just needs the coordinates for the tablet.  Sometimes that gets things working.

---

### Post by DaveHockley on 2013-03-29
Here are the results of the commands you gave...
Though I have no shame in admitting, I have absolutley no idea what the majority of it means!
```
Device 'HV Huion':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (284):    0
    Device Accel Constant Deceleration (285):    1.000000
    Device Accel Adaptive Deceleration (286):    1.000000
    Device Accel Velocity Scaling (287):    10.000000
    Device Product ID (274):    9580, 110
    Device Node (275):    "/dev/input/event6"
    Evdev Axis Inversion (288):    0, 0
    Evdev Axis Calibration (289):    <no items>
    Evdev Axes Swap (290):    0
    Axis Labels (291):    "Abs X" (279), "Abs Y" (280), "Abs Z" (281), "Abs Rotary X" (282), "Abs Pressure" (283)
    Button Labels (292):    "Button Left" (158), "Button Middle" (159), "Button Right" (160), "Button Wheel Up" (161), "Button Wheel Down" (162)
    Evdev Middle Button Emulation (293):    0
    Evdev Middle Button Timeout (294):    50
    Evdev Third Button Emulation (295):    0
    Evdev Third Button Emulation Timeout (296):    1000
    Evdev Third Button Emulation Button (297):    3
    Evdev Third Button Emulation Threshold (298):    20
    Evdev Wheel Emulation (299):    0
    Evdev Wheel Emulation Axes (300):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (301):    10
    Evdev Wheel Emulation Timeout (302):    200
    Evdev Wheel Emulation Button (303):    4
    Evdev Drag Lock Buttons (304):    0
dave@raven:~$ 
```

here's the result for ID# 11:

```
dave@raven:~$ xinput list-props 11
Device 'HV Huion':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (284):    0
    Device Accel Constant Deceleration (285):    1.000000
    Device Accel Adaptive Deceleration (286):    1.000000
    Device Accel Velocity Scaling (287):    10.000000
    Device Product ID (274):    9580, 110
    Device Node (275):    "/dev/input/event7"
    Evdev Axis Inversion (288):    0, 0
    Evdev Axis Calibration (289):    <no items>
    Evdev Axes Swap (290):    0
    Axis Labels (291):    "Abs X" (279), "Abs Y" (280), "Abs Pressure" (283)
    Button Labels (292):    "Button Left" (158), "Button Middle" (159), "Button Right" (160), "Button Wheel Up" (161), "Button Wheel Down" (162), "Button Horiz Wheel Left" (163), "Button Horiz Wheel Right" (164), "Button Side" (305), "Button Extra" (306), "Button Unknown" (277), "Button Unknown" (277), "Button Unknown" (277), "Button Unknown" (277)
    Evdev Middle Button Emulation (293):    0
    Evdev Middle Button Timeout (294):    50
    Evdev Third Button Emulation (295):    0
    Evdev Third Button Emulation Timeout (296):    1000
    Evdev Third Button Emulation Button (297):    3
    Evdev Third Button Emulation Threshold (298):    20
    Evdev Wheel Emulation (299):    0
    Evdev Wheel Emulation Axes (300):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (301):    10
    Evdev Wheel Emulation Timeout (302):    200
    Evdev Wheel Emulation Button (303):    4
    Evdev Drag Lock Buttons (304):    0


```

And finally, for ID#12:

```
dave@raven:~$ xinput list-props 12
Device 'HV Huion':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (284):    0
    Device Accel Constant Deceleration (285):    1.000000
    Device Accel Adaptive Deceleration (286):    1.000000
    Device Accel Velocity Scaling (287):    10.000000
    Device Product ID (274):    9580, 110
    Device Node (275):    "/dev/input/event8"
    Evdev Axis Inversion (288):    0, 0
    Evdev Axes Swap (290):    0
    Axis Labels (291):    "Rel X" (165), "Rel Y" (166), "Rel Horiz Wheel" (307)
    Button Labels (292):    "Button 0" (278), "Button Unknown" (277), "Button Unknown" (277), "Button Wheel Up" (161), "Button Wheel Down" (162), "Button Horiz Wheel Left" (163), "Button Horiz Wheel Right" (164)
    Evdev Middle Button Emulation (293):    0
    Evdev Middle Button Timeout (294):    50
    Evdev Third Button Emulation (295):    0
    Evdev Third Button Emulation Timeout (296):    1000
    Evdev Third Button Emulation Button (297):    3
    Evdev Third Button Emulation Threshold (298):    20
    Evdev Wheel Emulation (299):    0
    Evdev Wheel Emulation Axes (300):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (301):    10
    Evdev Wheel Emulation Timeout (302):    200
    Evdev Wheel Emulation Button (303):    4
    Evdev Drag Lock Buttons (304):    0


```

quite the long post!
Endev turns up alot here

---

### Post by Favux on 2013-03-31
So definitely on the evdev X driver.  :)

The question is do you want to experiment with the evdev, and maybe the Wacom, driver to see if you can get the tablet working on one of them?  Or do you want to go to the WizardPen driver?

If you want to try the evdev and/or Wacom driver first you need to check if you have the custom .conf directory and if not create it.  Use Nautilus (the file manager) to check if /etc/X11/xorg.conf.d exists.  If not create it with:
```
sudo mkdir /etc/X11/xorg.conf.d
```
For details on creating .conf files see:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev)

Then we need to try a custom snippet with the tablet coordinates and see what happens.  The pen has an absolute axis or Abs (Axis Labels) in the list-props output.  I'm not sure whether it is 10 or 11.

---

### Post by DaveHockley on 2013-04-14
Hi, sorry it took so long to reply!
I've been out of town for a while, had a few errands to run.
I ran the search to find /etc/X11/xorg.conf.d, but it's not there.
I'll have a shot at creating the conf file and get back to you.
I'm still a total learner with stuff like this, so I may be some time!

---

### Post by netmartin on 2013-05-27
Hello,

there is new driver in development for Huion 580 tablet at Digimend project. I actually have it working quite nicely. Hopefully it will be included in 3.11 mainline kernel and of course older kernels can be patched as well.

---

### Post by elclanrs on 2013-07-19
I got this tablet working with Digimend patch by Martin Rusko in kernel 3.9.10. I works very good, just plug and play. I packaged the patched kernel in debs if anybody wants to try it out. These are for Ubuntu 13.04 64bit.

[https://www.dropbox.com/s/v4vrardzpohwg2j/linux-image-3.9.10elclanrs_3.9.10elclanrs-10.00.Custom_amd64.deb](https://www.dropbox.com/s/v4vrardzpohwg2j/linux-image-3.9.10elclanrs_3.9.10elclanrs-10.00.Custom_amd64.deb)
[https://www.dropbox.com/s/otyo4cn4on3ohtl/linux-headers-3.9.10elclanrs_3.9.10elclanrs-10.00.Custom_amd64.deb](https://www.dropbox.com/s/otyo4cn4on3ohtl/linux-headers-3.9.10elclanrs_3.9.10elclanrs-10.00.Custom_amd64.deb)

---

### Post by blinkomania on 2013-09-05
Hi elclanrs, I tried your packaged kernal and I'm using 13.04 64bit. The mouse moves, but the pen fires about 10 left clicks all at once when you put the pen down. Are there settings anywhere else that I could play around with? I'm still messing around with 52-tablet.conf and 70-wizardpen.conf but to no avail.

---

