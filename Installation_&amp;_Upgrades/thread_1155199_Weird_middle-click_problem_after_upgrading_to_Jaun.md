---
title: "Weird middle-click problem after upgrading to Jaunty"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by fuxoft on 2009-05-10
Hello there,

I recently upgraded from 8.04 all the way to 9.04 and I now have rather weird problem with Gimp but it doesn't seem the new Gimp version inlucded in Jaunty is to blame.

I normally hold the middle mousebutton down and move the mouse to pan the image around in main Gimp window. However, when I try this in Jaunty, the image starts jumping all over the place as soon as I start moving it left or up. This happens even after I completely removed ~/.gimp-2.6 directory and restarted Gimp. Scrolling image using spacebar works as expected. I have Logitech G5 mouse and no special mouse configuration of any kind.

I think it might have something to do with the fact that middle-clicking on anything on Jaunty desktop in fact works as if I double-clicked the left mousebutton - I think this wasn't the case in 8.04 and I have no idea where this is controlled from. My xorg.conf doesn't contain anything at all about Mouse and System/Mouse dialog doesn't have any options for third mousebutton.

---

### Post by fuxoft on 2009-05-10
Wow, now I discovered I have the exactly same problem in Inkscape! So this is definitely not Gimp related.

How do I configure HAL devices? I have something called "Macintosh 2 button mouse compatibility" as one of my devices. I've never seen that in 8.06.

---

### Post by upchucky on 2009-05-10
not sure if this will help but in 8.04 i had to add some stuff to get my 7 button mouse working, there may be somewhere else u may need to add it if not in the xorg.conf file.

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons"       "7"
    Option         "ZAxisMapping"  "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

---

### Post by goldblattster on 2009-05-11
I need this fixed! *cries in corner*
bump :)

---

### Post by fuxoft on 2009-05-11
> **upchucky said:**
> not sure if this will help but in 8.04 i had to add some stuff to get my 7 button mouse working, there may be somewhere else u may need to add it if not in the xorg.conf file.

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "Buttons"       "7"
    Option         "ZAxisMapping"  "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

I'm afraid this won't help because in 9.04 there is no reference to any "InputDevice" in xorg.conf at all!

---

### Post by upchucky on 2009-05-11
so its not in xorg.conf. that was why i stated, if it is not there you will have to find out where the version you have does put the configuration info for the mouse.

perhaps make a new thread asking where Jaunty puts the file for mouse configuration?

---

### Post by kylehase on 2009-06-16
Did anyone find where Jaunty stores the mouse config?  I'm having problems with my mouse and I can't find any xorg.conf at all (clean minimal install with gnome)

---

### Post by jjalocha on 2009-06-17
The problem with the middle-click has been bugging me for quite some time (Jaunty) now on Firefox: When you middle-click a link, it should open in a new tab. This does sometimes work in Jaunty, but many times it doesn't.

---

