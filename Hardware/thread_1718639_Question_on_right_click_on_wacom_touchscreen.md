---
title: "Question on right click on wacom touchscreen"
date: 2011-03-31
forum: Hardware
---

### Post by catarano on 2011-03-31
I am running 10.04 on a touchsmart tm2

I would like to have a right click when holding the finger on the screen for a long time.

I tried to set it up using the mouse options for assistive technologies
    Preferences-->Assistive Technologies Preferences-->Mouse Accessibility
            -->Accessibility-->Trigger secondary click by holding down   
                 the primary button

It works with the touchpad and the mouse, but not with the touchscreen

on the other hand I get a right click when I tap with two fingers, but it is not very accurate and sometimes it gets messed up with scrolling.

Should I add some lines to 50-wacom.conf or to xorg.conf?

Thanks for any help

---

### Post by Favux on 2011-03-31
Hi catarano,

If you are using the default Wacom drivers that came with Lucid that might be part of the problem.  The X driver xf86-input-wacom-0.10.5 is pretty old (at 0.10.11 now) and updating it should give you some improvements in gestures.  Although if you do that you may want/need to update the Wacom kernel driver wacom.ko also.

Two finger double tap/right click is one finger down then tap with the second finger.

You shouldn't need to do anything to xorg.conf.  You could try some wacom.conf Options or xsetwacom commands adjusting the Taptime and such.

---

### Post by catarano on 2011-04-01
> **Favux said:**
> Hi catarano,

If you are using the default Wacom drivers that came with Lucid that might be part of the problem.  The X driver xf86-input-wacom-0.10.5 is pretty old (at 0.10.11 now) and updating it should give you some improvements in gestures.  Although if you do that you may want/need to update the Wacom kernel driver wacom.ko also.

Two finger double tap/right click is one finger down then tap with the second finger.

You shouldn't need to do anything to xorg.conf.  You could try some wacom.conf Options or xsetwacom commands adjusting the Taptime and such.

Thanks for your help, however that does not work

I the wacom module is the latest, since I have the package from the xorg-stable ppa and also the kernel module is the latest, sice I am running 2.6.38.1 and wacom is listed with lsmod.

I thought that this type of double tap = right click might work also with the touchpad

If I long press the left button on my touchpad, then it acts as a right click

however if I tap on the center of the touchpad and keep my finger pressed, it dous not act as a right click.

both the touchpad and the touchscreen give me a right click only if I tap simultaneously with two fingers.

I guess something in xorg might work....

However I just tried in 10.10 and saw that what you suggested does indeed work

so I must be something related to 10.04

will try with the official kernel and see what happens

in 10.10 also the assistive technology trick works with both touchpad and touchscreen

---

### Post by catarano on 2011-04-04
Actually your suggestion works also in 10.04 except in Nautilus

In my previous post I said that it did not work in 10.04 because my test was to simulate a right click in Nautilus

but instead your double tapping technique works in all of the other applications in 10.04 from the terminal to Firefox to Libreoffice

I tried to make a purge and then a reinstall of nautilus but without success

---

