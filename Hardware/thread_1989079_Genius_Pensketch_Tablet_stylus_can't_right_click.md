---
title: "Genius Pensketch Tablet stylus can't right click"
date: 2012-05-28
forum: Hardware
---

### Post by BcRich on 2012-05-28
Hi 
I'm trying to get my genius pensketch 9x12 tablet to work with a default ubuntu 12.04 installation. 
Just plugging the tablet into a usb seems to work for moving the pointer around and left clicking. however the pen has two other buttons that are supposed to be used for right clicking and middle mouse button. But neither of these buttons seem to work. 
Pressure sensitivity works in myPaint, but requires having to press really hard.
xinput list returns
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.0A    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:2007    id=10    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=11    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; PWC snapshot button                         id=8    [slave  keyboard (3)]
```running xinput list-props 11
```
Device '    Tablet PF1209':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Device Product ID (258):    21827, 66
    Device Node (259):    "/dev/input/event5"
    Evdev Axis Inversion (271):    0, 0
    Evdev Axis Calibration (272):    <no items>
    Evdev Axes Swap (273):    0
    Axis Labels (274):    "Abs X" (289), "Abs Y" (290), "Abs Pressure" (291)
    Button Labels (275):    "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (276):    0
    Evdev Middle Button Timeout (277):    50
    Evdev Third Button Emulation (278):    0
    Evdev Third Button Emulation Timeout (279):    1000
    Evdev Third Button Emulation Button (280):    3
    Evdev Third Button Emulation Threshold (281):    20
    Evdev Wheel Emulation (282):    0
    Evdev Wheel Emulation Axes (283):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (284):    10
    Evdev Wheel Emulation Timeout (285):    200
    Evdev Wheel Emulation Button (286):    4
    Evdev Drag Lock Buttons (287):    0

```
lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 1e3d:2095 Chipsbank Microelectronics Co., Ltd 
Bus 003 Device 005: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 004 Device 002: ID 1210:0002 DigiTech 
Bus 004 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 004 Device 004: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 007 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 007 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 004: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
Bus 008 Device 002: ID 1058:1140 Western Digital Technologies, Inc.
```
and when i try xinput set-button-map 11 1 2 3 4 5 (or even with device id 12) it only seems to have an effect on the first mapping, in other words the other button mapping seem to be ignored no matter what order i use.
I'm not using the wizardpen driver (**xserver-xorg-input-wizardpen)** because it might be problematic with 12.04 (from what I've read), so I think the tablet is using evdev which is version 2.7.0
If you could help me that would be awesome!

---

### Post by Favux on 2012-05-28
Hi BcRich,

Your tablet should be supported in Precise by the kernel and evdev:
```
Bus 007 Device 004: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
```
See:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)

Since there are two events (device ID #'s) presumably one is the tablet/pen and the other the mouse.  Do you have the tablet mouse?

So maybe the settings are getting conflated and we need to separate them out.

Have you set up a custom tablet.conf yet?  If not go ahead and do one followng:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_xf86-input-evdev)

Actually this gives me a chance to update that wiki page to bring it in line with the recent wacom page update.  So I'm glad for the opportunity.  Hope you don't mind being a tester.  :)

Fair warning.  I might be changing the names of the files and snippet identifiers etc. as we go along.

---

### Post by BcRich on 2012-05-28
Hi Faux
Thanks for the reply :)
I don't mind being a tester.
I added the file /etc/X11/xorg.conf.d/52-tablet-on-evdev.conf
which looks like this
```
Section "InputClass"
        Identifier "Custom evdev tablet options"
        MatchDriver "evdev"
        MatchProduct "     Tablet PF1209"

        # Apply custom Options below.
EndSection
```is that correct?
Nothings changed with the pen and tablet, this page is exactly my tablet [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_PF1209)
I do have the tablet mouse, which works perfectly i.e. mouse movement, left/right/middle click and wheel up and down

---

### Post by Favux on 2012-05-28
It's correct except you've used the <device name> instead of a keyword in the match.

I think maybe we'll go with 52-tablet.conf as the name, but obviously you don't need to rename.  The question is does the mouse identify itself as MatchIsPointer and the pen MatchIsTablet?  That would let us separate them.  So right now I've got:
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Graphics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```

---

### Post by BcRich on 2012-05-28
> **Favux said:**
> It's correct except you've used the <device name> instead of a keyword in the match.

I think maybe we'll go with 52-tablet.conf as the name, but obviously you don't need to rename.  The question is does the mouse identify itself as MatchIsPointer and the pen MatchIsTablet?  That would let us separate them.  So right now I've got:
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Graphics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection
```

sorry Favux, I don't know how to answer your question.
I've renamed the old file to 52-tablet.conf and replaced its contents with your code exactly. Is that what you were asking me?

---

### Post by Favux on 2012-05-28
Yes.  I meant let's find out if MatchIsTablet etc. works.

So now what happens if you add an Option for the pen snippet?
```
Section "InputClass"
        Identifier "Grahics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 3 2"
EndSection
```
Does that get the stylus buttons working correctly now?

---

### Post by BcRich on 2012-05-28
No changes.
The pen still does not right click or middle mouse button.
However prior to making the changes i noticed that the mouse started acting really strange, in fact it's pretty much non-operational at the moment. except for the wheel which seems to work sporadically.
don't know if it'll help but I use another mouse as my main mouse, so not having the tablet's mouse working is not big deal.
btw. do i need to restart my computer after editing the 52-tablet.conf file (that's what I've been doing)?

---

### Post by Favux on 2012-05-28
> No changes.
The pen still does not right click or middle mouse button.
Hmm.
> However prior to making the changes i noticed that the mouse started acting really strange, in fact it's pretty much non-operational at the moment. except for the wheel which seems to work sporadically.
Was that with the new tablet mouse snippet in place?
> btw. do i need to restart my computer after editing the 52-tablet.conf file (that's what I've been doing)? 
Yes.

With the two snippets do we see a difference in the **list-props** now?  Run **xinput list** again and make sure you have the two different device ID's.  Then repeat a **xinput list-props** for both.

The other thing to do is check the Xorg.0.log in /var/log and see if we now see the "Graphics tablet mouse" and "Graphics tablet pen" identifiers each on a separate event number.

---

### Post by BcRich on 2012-05-28
hi
xinput list
has not changed from my first post
>  	Quote:
 	 	 		 			 				However prior to making the changes i noticed that the mouse started  acting really strange, in fact it's pretty much non-operational at the  moment. except for the wheel which seems to work sporadically. 			 		 	 	 
Was that with the new tablet mouse snippet in place?
Yes, and even before that. I think it might have happened sometime during adding the 52-tablet file. but I'm not certain.

xinput list-props 11
```
Device '    Tablet PF1209':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Device Product ID (258):    21827, 66
    Device Node (259):    "/dev/input/event4"
    Evdev Axis Inversion (271):    0, 0
    Evdev Axis Calibration (272):    <no items>
    Evdev Axes Swap (273):    0
    Axis Labels (274):    "Abs X" (289), "Abs Y" (290), "Abs Pressure" (291)
    Button Labels (275):    "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (276):    0
    Evdev Middle Button Timeout (277):    50
    Evdev Third Button Emulation (278):    0
    Evdev Third Button Emulation Timeout (279):    1000
    Evdev Third Button Emulation Button (280):    3
    Evdev Third Button Emulation Threshold (281):    20
    Evdev Wheel Emulation (282):    0
    Evdev Wheel Emulation Axes (283):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (284):    10
    Evdev Wheel Emulation Timeout (285):    200
    Evdev Wheel Emulation Button (286):    4
    Evdev Drag Lock Buttons (287):    0

```
it looks the same to me.

xinput list-props 12
```
Device '    Tablet PF1209':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (267):    0
    Device Accel Constant Deceleration (268):    1.000000
    Device Accel Adaptive Deceleration (269):    1.000000
    Device Accel Velocity Scaling (270):    10.000000
    Device Product ID (258):    21827, 66
    Device Node (259):    "/dev/input/event5"
    Evdev Axis Inversion (271):    0, 0
    Evdev Axes Swap (273):    0
    Axis Labels (274):    "Rel X" (152), "Rel Y" (153), "Rel Vert Wheel" (266)
    Button Labels (275):    "Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (276):    0
    Evdev Middle Button Timeout (277):    50
    Evdev Third Button Emulation (278):    0
    Evdev Third Button Emulation Timeout (279):    1000
    Evdev Third Button Emulation Button (280):    3
    Evdev Third Button Emulation Threshold (281):    20
    Evdev Wheel Emulation (282):    0
    Evdev Wheel Emulation Axes (283):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (284):    10
    Evdev Wheel Emulation Timeout (285):    200
    Evdev Wheel Emulation Button (286):    4
    Evdev Drag Lock Buttons (287):    0
```
also looks the same

xinput list
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.0A    id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:2007    id=10    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=11    [slave  pointer  (2)]
&#9116;   &#8627;     Tablet PF1209                           id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; PWC snapshot button                         id=8    [slave  keyboard (3)]
```
also looks the same

> The other thing to do is check the Xorg.0.log in /var/log and see if we  now see the "Graphics tablet mouse" and "Graphics tablet pen"  identifiers each on a separate event number. 	
Graphics tablet mouse appears in Xorg.0.log but Graphics tablet pen is not in the file
see attachment.

---

### Post by Favux on 2012-05-28
Thanks.  Nice job.
> I think it might have happened sometime during adding the 52-tablet file. but I'm not certain.
Alright, that is likely the problem.  The Pen is being treated as a mouse I suppose.  But not quite sure why the custom .conf would do that if the MatchIsTablet is no good.

I'll look at the Xorg.0.log.  It should tell us what evdev snippets are matching also as a double check.

I'll have to sign off.  Need to get to grilling.  :)

---

### Post by BcRich on 2012-05-28
> **Favux said:**
> Thanks.  Nice job.

Alright, that is likely the problem.  The Pen is being treated as a mouse I suppose.  But not quite sure why the custom .conf would do that if the MatchIsTablet is no good.

I'll look at the Xorg.0.log.  It should tell us what evdev snippets are matching also as a double check.

I'll have to sign off.  Need to get to grilling.  :)
Thanks for the help Favux :)
I'm also signin out getting late in SA

---

### Post by Favux on 2012-05-28
OK, but I couldn't help myself and I looked at the Xorg.0.log.  At first blush it looks perfect, we seemed to have got it right.
```
[    13.106] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event4)
[    13.106] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[    13.106] (**)     Tablet PF1209: Applying InputClass "Grahics tablet pen"
[    13.106] (II) Using input driver 'evdev' for '    Tablet PF1209'
[    13.106] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.106] (**)     Tablet PF1209: always reports core events
[    13.106] (**) evdev:     Tablet PF1209: Device: "/dev/input/event4"
[    13.106] (**) evdev:     Tablet PF1209: ButtonMapping '1 3 2'
[    13.106] (--) evdev:     Tablet PF1209: Vendor 0x5543 Product 0x42
[    13.106] (--) evdev:     Tablet PF1209: Found absolute axes
[    13.106] (--) evdev:     Tablet PF1209: Found x and y absolute axes
[    13.106] (--) evdev:     Tablet PF1209: Found absolute tablet.
[    13.106] (II) evdev:     Tablet PF1209: Configuring as tablet
[    13.106] (**) evdev:     Tablet PF1209: YAxisMapping: buttons 4 and 5
[    13.106] (**) evdev:     Tablet PF1209: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.106] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.0/input/input4/event4"
[    13.106] (II) XINPUT: Adding extended input device "    Tablet PF1209" (type: TABLET, id 11)
[    13.106] (II) evdev:     Tablet PF1209: initialized for absolute axes.
[    13.106] (**)     Tablet PF1209: (accel) keeping acceleration scheme 1
[    13.106] (**)     Tablet PF1209: (accel) acceleration profile 0
[    13.106] (**)     Tablet PF1209: (accel) acceleration factor: 2.000
[    13.106] (**)     Tablet PF1209: (accel) acceleration threshold: 4
[    13.107] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/mouse1)
[    13.107] (II) No input driver specified, ignoring this device.
[    13.107] (II) This device may have been added with another device file.
[    13.107] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/event5)
[    13.107] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[    13.107] (**)     Tablet PF1209: Applying InputClass "Graphics tablet mouse"
[    13.107] (II) Using input driver 'evdev' for '    Tablet PF1209'
[    13.107] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.107] (**)     Tablet PF1209: always reports core events
[    13.107] (**) evdev:     Tablet PF1209: Device: "/dev/input/event5"
[    13.107] (--) evdev:     Tablet PF1209: Vendor 0x5543 Product 0x42
[    13.107] (--) evdev:     Tablet PF1209: Found 3 mouse buttons
[    13.107] (--) evdev:     Tablet PF1209: Found scroll wheel(s)
[    13.107] (--) evdev:     Tablet PF1209: Found relative axes
[    13.107] (--) evdev:     Tablet PF1209: Found x and y relative axes
[    13.107] (II) evdev:     Tablet PF1209: Configuring as mouse
[    13.107] (II) evdev:     Tablet PF1209: Adding scrollwheel support
[    13.107] (**) evdev:     Tablet PF1209: YAxisMapping: buttons 4 and 5
[    13.107] (**) evdev:     Tablet PF1209: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.107] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-3/7-3:1.0/input/input5/event5"
[    13.107] (II) XINPUT: Adding extended input device "    Tablet PF1209" (type: MOUSE, id 12)
[    13.107] (II) evdev:     Tablet PF1209: initialized for relative axes.
[    13.107] (**)     Tablet PF1209: (accel) keeping acceleration scheme 1
[    13.107] (**)     Tablet PF1209: (accel) acceleration profile 0
[    13.107] (**)     Tablet PF1209: (accel) acceleration factor: 2.000
[    13.107] (**)     Tablet PF1209: (accel) acceleration threshold: 4
[    13.107] (II) config/udev: Adding input device     Tablet PF1209 (/dev/input/mouse2)
[    13.107] (II) No input driver specified, ignoring this device.
[    13.107] (II) This device may have been added with another device file.
```
See:
```
[    13.106] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[    13.106] (**)     Tablet PF1209: Applying InputClass "Grahics tablet pen"
```
and
```
[    13.106] (**) evdev:     Tablet PF1209: ButtonMapping '1 3 2'
```
For the pen.  And for the mouse:
```
[    13.107] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[    13.107] (**)     Tablet PF1209: Applying InputClass "Graphics tablet mouse"
```

So can you check the stylus buttons on another release or OS.  Say Windows?

Trying to rule out a hardware problem.  I'll look at it a little more too.

---

### Post by BcRich on 2012-05-29
Hi Favux
i managed to test it on some one else's windows machine, and I'm sure it will come as no surprise to you that i was having the same problem.
I've had the pen for a few years but never actually used it cause i could never get it to work with ubuntu, so following your suggestion that it might be a hardware problem. i opened the pen and got to the buttons which had a major case of rust!
I managed to remove the rust and now the pen is working 100% for the first time in ubuntu. I'm guessing that software had nothing to do with it, as when i first tried the pen in 12.04 everything just worked (except for the barrel buttons, which were rusted internally).
Thanks a million for your help,
Sorry that I might not make much of a candidate as a tester anymore with a working model, but if there is anything else i can do to repay the favor please don't hesitate to mention it :)
thank you a million times over!

---

### Post by Favux on 2012-05-29
> I managed to remove the rust and now the pen is working 100% for the first time in ubuntu.
Outstanding!

Sure, if you have a little time I'd appreciate some more testing.

The list-props for 11 is a little different from 12 in that we see different event numbers and this line:
>     Evdev Axis Calibration (272):    <no items>
in 11 (the pen) and not 12 (the mouse).  Plus:
>     Axis Labels (274):    "Abs X" (289), "Abs Y" (290), "Abs Pressure" (291)
    Button Labels (275):    "Button Unknown" (261), "Button Unknown" (261), "Button Unknown" (261), "Button Wheel Up" (148 ), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
shows the pen has an Absolute axis while the mouse has:
>     Axis Labels (274):    "Rel X" (152), "Rel Y" (153), "Rel Vert Wheel" (266)
    Button Labels (275):    "Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148 ), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
a relative axis, which you would expect, and the initial buttons are assigned.

What I'd like to do is to try some changes on the snippet matches and see if they still work if you are game.

---

### Post by BcRich on 2012-05-29
> What I'd like to do is to try some changes on the snippet matches and see if they still work if you are game.
sure no prob :) let me know what u need?
btw. i think the mouse is totally keeshed, it didn't work either when i tried it on the win computer and the only buttons that work on ubuntu are scroll wheel up/down (which don't work all the time). sometimes when i press the scroll wheel up/down and move the mouse the cursor also moves on screen but that's also sporadic. so i'm guessing the mouse is probably also hardware defunct. but like i said the pen seems fine now :)

---

### Post by Favux on 2012-05-29
> i'm guessing the mouse is probably also hardware defunct.
That's a shame.  It would be fun to test with it too.  But as long as the Xorg.0.log etc. look good we're probably OK.

Alright let's try a new match and see if we can use the Vendor instead of the Product.  If it works you should see both of the new Identifiers in Xorg.0.log paired with the evdev ones.
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchVendor "UC-Logic"
#        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Graphics tablet pen"
        MatchIsTablet "on"
        MatchVendor "UC-Logic"
#        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 3 2"
EndSection
```

Thanks for helping.  :)

---

### Post by BcRich on 2012-05-29
changed 52-tablet.conf and here's the log file attached. do u need another 
xinput list props readout?
```
Device '    Tablet PF1209':
    Device Enabled (142):    1
    Coordinate Transformation Matrix (144):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (355):    0
    Device Accel Constant Deceleration (356):    1.000000
    Device Accel Adaptive Deceleration (357):    1.000000
    Device Accel Velocity Scaling (358):    10.000000
    Device Product ID (258):    21827, 66
    Device Node (259):    "/dev/input/event6"
    Evdev Axis Inversion (359):    0, 0
    Evdev Axis Calibration (360):    <no items>
    Evdev Axes Swap (361):    0
    Axis Labels (362):    "Abs X" (305), "Abs Y" (306), "Abs Pressure" (307)
    Button Labels (363):    "Button Unknown" (349), "Button Unknown" (349), "Button Unknown" (349), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151)
    Evdev Middle Button Emulation (364):    0
    Evdev Middle Button Timeout (365):    50
    Evdev Third Button Emulation (366):    0
    Evdev Third Button Emulation Timeout (367):    1000
    Evdev Third Button Emulation Button (368):    3
    Evdev Third Button Emulation Threshold (369):    20
    Evdev Wheel Emulation (370):    0
    Evdev Wheel Emulation Axes (371):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (372):    10
    Evdev Wheel Emulation Timeout (373):    200
    Evdev Wheel Emulation Button (374):    4
    Evdev Drag Lock Buttons (375):    0

```
thats for device 11, nothings changed for xinput list. however the button mapping on the pen has changed middle mouse button and right click have swapped. but the pen is workin fine still

---

### Post by Favux on 2012-05-29
Thanks.  Looks like the vendor match didn't work.  The keywords are case sensitive.  Could you check what you get with?
```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event6) | grep manufacturer
```
Assuming the stylus is still on event6.

---

### Post by BcRich on 2012-05-29
hi
i think it is still on event6
 running your command
```
 ATTRS{manufacturer}=="   "
    ATTRS{manufacturer}=="Linux 3.2.0-23-generic ohci_hcd"
```
running input-events on event 6 (from input utilities) returns
```
/dev/input/event6
   bustype : BUS_USB
   vendor  : 0x5543
   product : 0x42
   version : 256
   name    : "    Tablet PF1209"
   phys    : "usb-0000:00:16.0-3/input0"
   uniq    : ""
   bits ev : EV_SYN EV_KEY EV_ABS EV_MSC

waiting for events
timeout, quitting

```
and lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
Bus 004 Device 002: ID 1210:0002 DigiTech 
Bus 007 Device 004: ID 5543:0042 UC-Logic Technology Corp. Tablet PF1209
Bus 004 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 004 Device 004: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 007 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 007 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 009 Device 002: ID 1058:1140 Western Digital Technologies, Inc.
```
does that mean it's still on event6?
One thing I forgot to mention, was after making the changes to the 52-tablet file and restarting, all of my usb devices hung at the login screen. until i unplugged the tablet, then replugged it in again and all the devices seemed to initialize properly (including the tablet), any idea why it would do that?

---

### Post by Favux on 2012-05-29
Well that shoots down that idea.  I was hoping we could come up with a match that didn't require the user finding a keyword, something like:
```
        MatchVendor "UC-Logic|KYE"
```
but if MatchVendor is matching to manufacturer yours is blank so it doesn't work.  We'd have to make a udev rule and there is no point to that.

Thanks for testing it and looking into it further.
> after making the changes to the 52-tablet file and restarting, all of my usb devices hung at the login screen. until i unplugged the tablet, then replugged it in again and all the devices seemed to initialize properly (including the tablet), any idea why it would do that? 
No, that shouldn't happen.  Let me know if it happens again.

One final thing to test.  Starting with X Server 1.10 they added a new match called MatchDriver.  Let's see if we can use that instead of invoking the evdev driver again.
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
	MatchDriver "evdev"
        MatchIsPointer "on"
        MatchProduct "PF1209"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Graphics tablet pen"
	MatchDriver "evdev"
        MatchIsTablet "on"
        MatchProduct "PF1209"
#        MatchDevicePath "/dev/input/event*"
#        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 3 2"
EndSection
```
If it works your pen buttons should still be switched.  :)

---

### Post by BcRich on 2012-05-29
Hi,
I edited the file and my pen buttons are back to the previous configuration, meaning they have changed.
My usb devices hung again when i rebooted and got to the login screen, had to unplug and replug the tablet in order for all devices to initialize properly.
thanks for the help favux :)

---

### Post by Favux on 2012-05-29
Alright, sounds like MatchDriver didn't work either.  But I would appreciate you posting the Xorg.0.log with those snippets active so I can take a peek.
> My usb devices hung again when i rebooted and got to the login screen, had to unplug and replug the tablet in order for all devices to initialize properly.
Do you have the tablet plugged into a hub.  That may be the problem.  I don't think anything we've done should be causing that since we got a clean Xorg.0.log with the first custom 52-tablet.conf.  But I'll look at it some more.  Do you get the hang with the original 52-tablet.conf?

---

### Post by BcRich on 2012-05-29
here's the current log file,
i'll change back to the original 52-tablet.conf and let u know if i still get the hanging problem

---

### Post by BcRich on 2012-05-29
Hi 
My tablet is plugged straight into the front panel of my desktop, no hub.
i changed my 52-tablet.conf back to 
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Grahics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 3 2"
EndSection
```
and still getting the hang. i could try another usb port, if u think it might help?
it's not a really big prob for me cause I'll probably not have my tablet plugged in most of the time and only plug it in after I've logged in. do u want to try fix it?

---

### Post by Favux on 2012-05-29
Great!  According to the Xorg.0.log the MatchDriver match worked!
> [    71.042] (**)     Tablet PF1209: Applying InputClass "evdev tablet catchall"
[    71.042] (**)     Tablet PF1209: Applying InputClass "Graphics tablet pen"
with
> [    71.042] (**) evdev:     Tablet PF1209: ButtonMapping '1 3 2'
and
> [    71.042] (**)     Tablet PF1209: Applying InputClass "evdev pointer catchall"
[    71.042] (**)     Tablet PF1209: Applying InputClass "Graphics tablet mouse"

---

### Post by Favux on 2012-05-29
Yes, please try another port.

I'm wondering if it isn't the tablet itself causing the hang.  If you still have the hang with the original 52-tablet.conf try  You might want to try commenting out the mouse snippet and see if that changes anything.  Then try commenting all the contents out and see if that makes a difference.  If you still have the hang I'd be more inclined to blame the tablet.  If there was a problem with the .conf it should break X so the gui doesn't start.

But then what?  Try removing the .conf file and the /etc/X11/xorg.conf.d directory and see if the hang goes away?  The directory shouldn't be a problem.  But who knows?

---

### Post by BcRich on 2012-05-31
Hi Favux
I hope you'll be happy to know that I tried pluggin the table into another USB port at the back of my computer (it's a USB 3 port but I don't think that really makes a diff?) and when I started up my computer with the original 52_tablet.conf, everything worked perfectly!
Perhaps the two fronts ports (which is where I had my tablet plugged) are on some sort of internal mini-hub, I really don't know. But I'm really grateful for your help in getting it to work.
I've included the log file in it's current state where everything is working 100%
Once again thanks a mill for the help :popcorn:

---

### Post by Favux on 2012-05-31
> I tried pluggin the table into another USB port at the back of my computer (it's a USB 3 port but I don't think that really makes a diff?) and when I started up my computer with the original 52_tablet.conf, everything worked perfectly!
Great!  lol  Now I am confused.  Is there another line for the tablet appearing in **xinput list**?

The Xorg.o.log seems to show another device input event.  Now that the tablet is maybe getting full power?  And everything is configured by the evdev.conf.  No indication of the 52-tablet.conf.  Shoot, the moment of clarity disappears in a puff of smoke.
> Perhaps the two fronts ports (which is where I had my tablet plugged) are on some sort of internal mini-hub
Right, the front ports likely go through a different usb controller than the rear ones.

I think it is usually a power issue and not just due to the power difference of usb 1.1 or usb 2.0.  I think some external hubs, especially when loaded, tend not to supply the power they claim.  It could also be a connection problem, with poor port design or port manufacturing.  Or noise or a bad internal connection.  Maybe a failing component like a capacitor.

So I try to remember to suggest plugging in directly and also trying different ports.

---

### Post by BcRich on 2012-05-31
doh! I'm such a putz :oops:
I sent you the wrong log file, that one was from my 10.10 installation. Sorry.
I'm currently booted in 10.10 and can't reboot into 12.04 so I'm sending you the 12.04 log file which is from the last time I booted into that OS and everything was working fine i.e. the usb devices were NOT hanging at login and the tablet was working 100%.
Sorry about the confusion, hope you didn't spend a long time pondering over it?

---

### Post by Favux on 2012-05-31
Now that Xorg.0.log is pretty!  Thanks.

And that's with the two MatchDriver snippets, correct?  So we're good to go and we've got ourselves a working custom .conf.  Sweet.

I'm sure I would have notice the Maverick X server and kernel versions at the top of that Xorg.0.log.  Eventually.  :)

---

### Post by BcRich on 2012-05-31
> **Favux said:**
> Now that Xorg.0.log is pretty!  Thanks.

And that's with the two MatchDriver snippets, correct?  So we're good to go and we've got ourselves a working custom .conf.  Sweet.

I'm sure I would have notice the Maverick X server and kernel versions at the top of that Xorg.0.log.  Eventually.  :)
lol, don't know what i was thinking :D
yea that's with the two snippets, here's the 52-tablet.conf
```
Section "InputClass"
        Identifier "Graphics tablet mouse"
        MatchIsPointer "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.

EndSection

Section "InputClass"
        Identifier "Grahics tablet pen"
        MatchIsTablet "on"
        MatchProduct "PF1209"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        # Apply custom Options below.
        Option "ButtonMapping" "1 3 2"
EndSection
```
all the best :popcorn:

---

