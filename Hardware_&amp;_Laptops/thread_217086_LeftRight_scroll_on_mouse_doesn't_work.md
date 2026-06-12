---
title: "Left/Right scroll on mouse doesn't work"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by ORBiTrus on 2006-07-16
I have two computers - one is has an MX510 under Gentoo, and I'm using the evdev Xorg driver to get it working.  I've done this before, I should know how it works, right?  Hah.

OK, so the other is running Dapper (the intersection of the set of all operating systems on a machine-by-maching basis is empty for my adminstered 9 systems) and I'm trying to set up a Microsoft Comfort Optical Mouse 3000, as this was the preferred mouse by this system user.

Well, the default (ExplorerePS/2) recognized the thumb button as Button 9, but the scroll wheel supports up/down left/right.  The Up/Down works, the Left/Right doesn't.  So, I figure I'll switch to evdev since it has better luck with these things.

I run through the whole udev rule hack business, replug the mouse - device /dev/input/Comfort_Mouse shows up, a cat as root reveals output when the left/right scroll buttons are hit.

Set up the xorg.conf file, and ...
```
preinit returned null
No configured core pointer
```

OK, gg: the error, and change from using Device /dev/input/Comfort_Mouse to Name Microsoft Optical .....

Still the same error.

Anyone know how to fix this?  It's rather annoying.

Oh, if I use the evdev driver with Device /dev/input/mice or /dev/input/mouse0 or ... and no Name, it still fails.  Eh?

For the record, the relevant section reads:

```
Section "InputDevice"
  Identifier "MsComfortOpticalMouse3000"
  Driver "evdev"
  Option "Device" "/dev/input/Comfort_Mouse"
EndSection
```


Edit:
No, wait.... Name did work, after I replugged the device in.  Ah, so the evdev driver just reads the device list and pulls up the device node, which of course, was still directing to /dev/input/Comfort_Mouse even after I removed the udev rule, and interpretting this as an illegal Device name.  But now that I have it as event4 (from replugging the device), it comes out A-OK.  No X error messages.

Still, no left/right scroll.  Any ideas from anyone?

---

### Post by Whatevs79 on 2006-09-16
Just got mine working...

The process was pretty much:
[FONT=Courier New]cat /proc/bus/input/devices[/FONT]
Note the [FONT=Courier New]NAME[/FONT] (so you don't have to mess with udev rules) and [FONT=Courier New]REL[/FONT] fields. REL is a hex number that you then have to decode into binary and note which places have 1's (with the low order [1's place] bit being bit 0).

For the MS COM3K:
[FONT=Courier New]I: Bus=0003 Vendor=045e Product=00d1 Version=0120
N: Name="Microsoft Microsoft Optical Mouse with Tilt Wheel"
P: Phys=usb-0000:00:11.2-1/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 event3 ts1
B: EV=7
B: KEY=170000 0 0 0 0 0 0 0 0
B: REL=1c3[/FONT]
0x1c3 = 0001 1100 0011 = bits 1,2,6,7,8

[FONT=Courier New]grep 'define REL_' /usr/include/linux/input.h[/FONT]
Look up the bit numbers in this list to see which REL events your mouse claims to generate.

For the MS COM3K it's:
[FONT=Courier New] REL_X, REL_Y, REL_HWHEEL, REL_DIAL, REL_WHEEL[/FONT]

REL_X and REL_Y are the regular cursor movement events, so we can ignore those. Refering to the *Relative Axis Configuration* section of [FONT=Courier New]evdev(4)[/FONT], I mapped all of the other relative axes to mouse buttons beginning with 10, and then ran [FONT=Courier New]xev[/FONT] to see what each axis actually was. Based on that experiment I got this [FONT=Courier New]xorg.conf[/FONT] section that works:
[FONT=Courier New]Section "InputDevice"
   Identifier      "Configured Mouse"
   Driver              "evdev"
   Option              "CorePointer"
           Option              "Name"          "Microsoft Microsoft Optical Mouse with Tilt Wheel"
   Option              "DIALRelativeAxisButtons"         "7 6"
           Option              "WHEELRelativeAxisButtons"       "4 5"
   Option              "ZAxisMapping"   "4 5 6 7"
EndSection[/FONT]

The [FONT=Courier New]WHEELRelativeAxisButtons[/FONT] option should be unneccessary, and I suspect the [FONT=Courier New]DIALRelativeAxisButtons[/FONT] line could more properly be replaced with:
      [FONT=Courier New]Option          "HWHEELRelativeAxisMap"        "3"[/FONT]
but it works as is, and I'm bored with this little adventure for now...

Oh, and it sounds like you already know this, but don't forget to change the Firefox/Thunderbird config keys:
[FONT=Courier New]mousewheel.horizscroll.withnokey.action         user set     integer     0
mousewheel.horizscroll.withnokey.numlines     user set     integer     4[/FONT]

-Evan

---

### Post by etnlIcarus on 2006-09-29
Thank you so much I'd been trying to get my CM3000 working for the better part of the last week.

However, i still have one quarrel: on Windows, I had the Intellimouse drivers set up so that the side/thumb button emulated the middle-click, "autoscroll", function. I did this because my middle finger cramps up from middle clicking all the time. Is there any way to make the thumb button emulate the middle click button and not the left click button in Ubuntu?

Thanks.
Ick

---

### Post by superm1 on 2007-02-16
Thanks a bunch for this!  Here is what I use for my mx510 now:

Section "InputDevice"
          Identifier  "Mouse1"
          Driver      "evdev"
          Option      "Name" "Logitech USB-PS/2 Optical Mouse"
          Option      "WHEELRelativeAxisButtons" "4 5"
          Option      "ZAxisMapping" "4 5"
          Option      "Resolution" "800"
EndSection

---

### Post by etnlIcarus on 2007-05-02
*bump*

I've been using the evdev mouse driver with my MS Comfort Mouse 3000 for the last two incarnations of Ubuntu without a problem. However, since upgrading to feisty, the horizontal scrolling activated by the mouse's 'tilt-wheel' has become inverted.

I've tried, these variations:

- Option "DIALRelativeAxisButtons" "7 6"
- Option "DIALRelativeAxisButtons" "6 7"
- Option "HWHEELRelativeAxisMap" "7 6"
- Option "HWHEELRelativeAxisMap" "6 7"

And I've tried 
- Option "ZAxisMapping" "4 5 6 7", with the 6 and 7 inverted.

After restarting X, the result is always the same: left scrolls right, while right scrolls left.

As a stop-gap measure, I've set Firefox numlines to a negative integer but, obviously, that doesn't translate to anyting else on the PC and it's becomming very annoying, very quickly.

Any help would be greatly appreciated.
Thanks.

Edit: Never mind, I had a brief attack of *intelligence* and changed my xorg to:
Option "HWHEELRelativeAxisButtons" "7 6"

Well, thanks for reading my blabering idiocy anyway. :P

---

### Post by Kossilar on 2008-04-12
Hey thanks for the info guys.

Using this information I've managed to get my tilt wheel working in firefox. But how do I set it up so that I can assign the mouse stroke to a particular action such as switching desktops?

Any ideas?

Also, this broke the thumb button. We really need to figure out a way to assign these special buttons to custom actions.

...

Wait I'm a n00b. It seems to be working fine now. Thanks everybody!

---

