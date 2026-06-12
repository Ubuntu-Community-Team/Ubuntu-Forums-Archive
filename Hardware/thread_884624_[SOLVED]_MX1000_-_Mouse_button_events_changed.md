---
title: "[SOLVED] MX1000 - Mouse button events changed?"
date: 2008-08-09
forum: Hardware
---

### Post by EnlistedSquire on 2008-08-09
Hi,

I posted something similar at the end of [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=767206") thread but it seems to have died off.

I used the How To in the above thread to set up my stand alone, RF (not bluetooth) Logitech MX1000 after updgrading to Hardy and it worked fine.

However, I came back to my PC after a few days of not using it earlier last week and it's gone totally to pot. I can no longer get the horizontal scrolling to work - the left and right mouse wheel buttons don't give a button number in xev and they seem to have picked up the same output as the volume + and - on my keyboard (which have been working fine from day one).

The cruise buttons now give the same button number as scrolling the mouse wheel up and down (buttons 4 and 5) when they were previously different as I had the cruise buttons assigned to Page Up and Page Down. I tried install lomoco and disabling SmartScroll and the cruise buttons no longer get a button assignment in xev either. This is what xev gives for my cruise button with SmartScroll disabled:

```
MotionNotify event, serial 31, synthetic NO, window 0x3400001,
    root 0x1a6, subw 0x3400002, time 867717, (64,36), root:(1775,221),
    state 0x10, is_hint 0, same_screen YES
```

And this is what I get with SmartScroll enabled:

```
ButtonPress event, serial 31, synthetic NO, window 0x3600001,
    root 0x1a6, subw 0x3600002, time 941972, (27,39), root:(1739,90),
    state 0x10, button 4, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3600001,
    root 0x1a6, subw 0x0, time 941972, (27,39), root:(1739,90),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2064
```

Here is what my previously working xorg.conf looks like:

```
Section "InputDevice"
	Identifier	"Logitech MX1000"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event2" 
	# If your event handler is something other than event8, 
	# change it to the appropriate value
	Option 		"RelHWHEELMapTo"	"Buttons 7 6"
EndSection
```

Can anyone offer an idea as to what's gone wrong and how to fix it? I've tried powering everything off to give the mouse a hard-reset and started these instructions totally from scratch from a default xorg.conf.

I had a go using BtnX but couldn't get the horizontal mouse wheel action to work (I assume because it's not compatible with evdev so I was using the standard mouse driver).

Thanks.

---

### Post by EnlistedSquire on 2008-08-10
Bump!

---

### Post by doug1212 on 2008-08-10
Until last month I had a MX1000 and had no joy setting up on Hardy as I was getting double output for the extra buttons (kernel problem?).
I am now back using my trusty MS comfort mouse.
While trawling on google I did find this:
[HTML]http://mxlaser.hjcms.de/?ref=welcome&lang=en[/HTML]
Looks like a dev who fed up with looking and fixed it?

Doug

---

### Post by EnlistedSquire on 2008-08-10
> **doug1212 said:**
> Until last month I had a MX1000 and had no joy setting up on Hardy as I was getting double output for the extra buttons (kernel problem?).
I am now back using my trusty MS comfort mouse.
While trawling on google I did find this:
[HTML]http://mxlaser.hjcms.de/?ref=welcome&lang=en[/HTML]
Looks like a dev who fed up with looking and fixed it?

Doug

Thanks doug1212, I'll have a look at that link. Bizarrely, double output of the up cruise button does seem to be happening for me sometimes, but not always.

I should mention,  I had this set up flawlessly in Gutsy but an upgrade stopped the mouse working completely. The set up I'm working with at the moment is a fresh install of Hardy on the same rig.

Cheers.

---

### Post by EnlistedSquire on 2008-08-15
OK, I got round to looking at that link and it's waaaaay over my head.

This is the first step (after downloading the driver which I did manage :) ) :

> Before you start please make sure that following points are right.

   1. The kernel source exists and already compiled or precompiled.
   2. The hidraw and hiddev Kernel support was configured as modul. the mxlaser must initial before usbhid or hidraw to reserve the usb device address.
```
grep -e HIDRAW -e USB_HID /usr/src/linux-`uname -r`/.config
# CONFIG_HIDRAW is not set
CONFIG_USB_HID=m
# CONFIG_USB_HIDINPUT_POWERBOOK is not set
CONFIG_USB_HIDDEV=y
```

I assume I'm meant to plug the line
```
grep -e HIDRAW -e USB_HID /usr/src/linux-2.6.24-19-generic/.config
```
into a terminal but I don't get the output
> # CONFIG_HIDRAW is not set
This is what I get instead:
> grep: /usr/src/linux-2.6.24-19-generic/.config: No such file or directory

Help? :confused:

---

### Post by EnlistedSquire on 2008-08-15
Back to normal.

I found this Launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159824]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159824")

I blacklisted the module lmpcm_usb and all is now right with the world.:)

---

