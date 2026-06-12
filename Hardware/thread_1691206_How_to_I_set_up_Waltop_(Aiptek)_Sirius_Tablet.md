---
title: "How to I set up Waltop (Aiptek) Sirius Tablet?"
date: 2011-02-19
forum: Hardware
---

### Post by user333 on 2011-02-19
I recently purchased a new [Sirius graphics tablet]("http://www.aiptek.com/Tablets/Sirius/Features/") from Aiptek. I got the tablet to work in Windows 7, but I would like it to work in Ubuntu. The pointer works, but there is not pressure, and some applications can't use it. The pen is as smooth as ever until there is a click, then it freezes.

I installed the Aiptek drivers, but I don't this tablet really is an Aiptek tablet(they resell waltop tablets). The waltop site gives a modified version of the wacom drivers, but I already installed them for another tablet, and they aren't working either.

Is there a way I can manually make a driver? This tablet doesn't seem to fit into any of the types listed in the Ubuntu online manual.


Running lsusb gives:
```
Bus 001 Device 003: ID 172f:0502 Waltop International Corp.  
```

---

### Post by Favux on 2011-02-19
Hi user333,

If you are in Lucid you want the WizardPen drivers.  See the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").

---

### Post by user333 on 2011-02-22
Thank's for the link! That guide helped a lot :) The pen kind of  "works" now. At least the pointing and pressure works. 

Just so you know, I'm not using the more popular slim tablet (used in your tutorial). I'm using a Sirius tablet. It has 4000 lpi, two touch areas, 8 buttons, 4 modes (I'm not sure what they do), tilt sensitivity, and uses a battery free pen.

The problem I'm having now is that clicking won't work (Taping to click or the two buttons on the pen). Also, tilt sensitivity is gone. Is it possible to enable these things?

Here's my conf file:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option        "Device"    "/dev/input/event7"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "19903"
    Option        "BottomY"    "11884"
    Option "TopZ" "0" Option "BottomZ" "1023"
    Option  "Mode"  "Absolute"

EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

It's not really important, but is it also possible to enable the touch wheels? They are two small touch pads you swirl you finger around to zoom in or out. They function the same as a scroll wheel.

---

### Post by Favux on 2011-02-22
Let's start by cleaning up your first snippet so it looks like:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchProduct "WALTOP"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
    Option        "TopX"        "0"
    Option        "TopY"        "0"
    Option        "BottomX"    "19903"
    Option        "BottomY"    "11884"
    Option "TopZ" "0"
    Option "BottomZ" "1023"
    Option  "Mode"  "Absolute"
EndSection

```
The event7 line should be duplicating the event* line and you had two Options doubled up.

The hotkey buttons and touch pads, etc. on the tablet don't work.  Apparently no one has written the code to support them.

---

### Post by user333 on 2011-02-22
No clicking still, but I do have a middle-mouse-button, and a right-click button now. Is there a way to assign a tap to mean a click?

Also, sometimes when I move my pen around it is locked on a click, so it always draws even with the pen hovering over the tablet.

---

### Post by Favux on 2011-02-22
Let's try adjusting you pressure threshold up.  Change TopZ to:
```
    Option "TopZ" "20"

```

---

### Post by user333 on 2011-02-22
That doesn't seem to change anything, better or worse...

---

### Post by Favux on 2011-02-23
Not sure.  Nothing is jumping out in the *man wizardpen* I have posted on the HOW TO or in the wiki:  [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)  You could enter *man wizardpen* in a terminal and see if it has been updated with anything new.  And also check the README etc.

We could try looking at xinput list-props and see if there is anything we can change.  Enter in a terminal:
```
xinput list
```
And find the stylus "device name".  Then enter:
```
xinput list-props "device name"
```
Post the output.

---

### Post by user333 on 2011-02-23
Here is the result:
```

    Device '         WALTOP     Batteryless Tablet ':
    Device Enabled (118):    1
    Device Accel Profile (249):    0
    Device Accel Constant Deceleration (250):    1.000000
    Device Accel Adaptive Deceleration (252):    1.000000
    Device Accel Velocity Scaling (253):    10.000000

```And here all of my pointing devices from xinput list if this would help:
```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=10    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=11    [slave  pointer  (2)]
&#9116;   &#8627;          WALTOP     Batteryless Tablet      id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]

```

---

### Post by Favux on 2011-02-23
Nope, nothing on button mapping.  Right now it sounds like its set up as a click drag.  So that's probably how the wizardpen driver is handling it for some reason.  Others weren't reporting that that I recall.  Well it's sort of lucky that the Waltop even works with it.

I guess you could try the Aiptek driver and see if your Waltop works and/or works better with it.   Some folks have reported luck with it and their Waltops in Lucid.

---

### Post by user333 on 2011-02-24
Thanks for all you help! I guess I'll just have to play with the drivers a little bit more. And yes, I think the pen is on a click-drag.

The tablet is hardly a few months old(since it was first made available), so maybe if I just wait it will be supported later on.

If I do figure out a way to make this work, where should I post a guide? On a private site, here in the forums, or in the community wiki documentation?

---

### Post by Favux on 2011-02-24
Good luck!

Choice is yours but I'd start a new thread in laptop & hardware and put the HOW TO in the first post.

---

### Post by user333 on 2011-04-07
Well, I have good news :) The tablet works perfectly in Natty Beta 1, at least is appears to. I have yet to install gimp or mypaint to test pressure. I'm running Natty on a old laptop to test hardware comparability, and so far all my hardware works, even stuff that never did before, like this tablet :)

---

### Post by Favux on 2011-04-07
Great!  :)

Looks like Nikolai's kernel patches are doing the trick.

---

### Post by user333 on 2011-04-08
It seems that although EVERYTHING else works, as far as touch areas, buttons, clicking, dragging, pressure, zoom, and pan work, but tilt does not. When the pen is tilted in a painting program, the brush jumps up to the top of the screen depending on how much you tilt the pen, making it useless unless tilt can be disabled. I'm using mypaint, but maybe gimp will be better. For now all the tablet can do is be a mouse replacement, or make very nice paintings that look like bar codes. Oh well. Whatever was done though was an improvement :)

Do you know of a way to totally disable tilt?

---

### Post by Favux on 2011-04-09
That's not good.
> Do you know of a way to totally disable tilt? 
No.  I suppose there may be a way but I don't know what it is.  Looking at wcmUSB.c in /src in the xf86-input-wacom folder I see:
> 	{ WALTOP_VENDOR_ID, 0x502, 200000, 200000, &usbIntuos4   },
Apparently your model Waltop is paired to the Intuos4 which I'm pretty sure does have tilt.

So the key question becomes is your model Waltop tablet suppose to support tilt for the stylus?

If not this is a bug and we need to pair it up with a Wacom tablet that doesn't have tilt.  I'm not quite sure how the static struct there works so that might become an adventure.

---

### Post by user333 on 2011-04-10
> So the key question becomes is your model Waltop tablet suppose to support tilt for the stylus?
Yes, basically that is all that's wrong. All other features work. The problem is that the tilt is that the computer miss-understands it, and maps tilt to position rather than changing the brush angle. Would it be possible to create a custom driver based on the Intuos driver that doesn't have tilt?

> 
Apparently your model Waltop is paired to the Intuos4 which I'm pretty sure does have tilt.
Yes, the tablet is almost a "clone" of the intuos.

---

### Post by Favux on 2011-04-10
Just to be sure:

Your Waltop tablet supports tilt?  That's what Waltop, or whatever the rebrander's name is, says?

If so:
> The problem is that the tilt is that the computer miss-understands it, and maps tilt to position rather than changing the brush angle.
I think that might mean the xf86-input-wacom driver is treating the stylus tilt as a Wacom mouse/puck tilt not stylus tilt.  If so that's a "bug" in the code and we should report that to linuxwacom-discuss to get it fixed:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)
> Would it be possible to create a custom driver based on the Intuos driver that doesn't have tilt?
I think so.  That's what I was planning to try because I didn't realize Waltop's supported tilt.  Looking at the static struct in wcmUSB.c I was wondering what would happen if we changed *&usbIntuos4* to *&usbBamboo*.  I'm pretty sure the Bamboo doesn't have tilt.  And hoping the difference in resolution isn't a problem.

---

### Post by user333 on 2011-04-11
> Your Waltop tablet supports tilt?  That's what Waltop, or whatever the rebrander's name is, says?
Yes. It definitely supports tilt. It doesn't say so on the site, but I know from using it.

I'll work on filing a bug later. Just so you know, the Bamboo is not nearly the size of this tablet. The Sirius is 4000lpi and 10"x6" active area, while the Bamboo is 2540lpi and 5.8"x3.6" active area.

---

### Post by user333 on 2011-05-15
Well, it work's fine in Natty now as far as I can tell. Tilt still doesn't work right, but it now is mapped different so if you disable tilt, the pen works fine rather than jump around. It's not a big deal either, because in most cases you NEVER need it. I've tested it with Gimp and MyPaint.  I'm using it on the 64 bit version of 11.04, so I'll have to see if it works on 32 bit as well.

---

### Post by user333 on 2011-10-14
Well, now with 11.10 it does not work :(

---

