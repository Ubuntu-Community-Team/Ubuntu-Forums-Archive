---
title: "Touchpad configuration help needed."
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by Jack.Straw on 2007-07-30
Hi.  I'm very happy to say that all the hardware in my Toshiba Satellite (M105-S3041) worked with ubuntu feisty "out-of-the-box".  Well done!  

However, i'm finding the synaptics touchpad functionality not up to the windows standards that i am used to.  I've tried adjusting things within ubuntu's touchpad configuration utility and i've also installed qsynaptics and tried adjusting it using that.  Unfortunately i'm still having a few touchpad issues that are large enough to make me give up on linux if i can't get them resolved.  It's just too frustrating.

1) Tap sensitivity:  I'm constantly clicking on things that i don't mean to, especially in firefox, because of the tap sensitivity.  Very often when i single tap it registers two taps.  When closing a maximized window I very often accidentally close the maximized window behind it as well.  Is there a way to adjust the tapping sensitivity?  So far i've only been able to find a "tapping time".   There is also an "enable faster tapping" checkbox that doesn't seem to effect me one way or the other.

2) Dragging items:  When dragging a window or icon around it is common for me to reach the edge of the touchpad before i get the object where i want it.  In windows i have things setup so that a double-tap+drag locks onto the object and it isn't released until another single-tap is made.  This allows me to lift my finger from the pad and replace it without loosing my hold on the object.  It is especially useful to me in programs like Photoshop.  Is there a way to enable this function in ubuntu?

3) When i reach the edge of the touchpad i expect the cursor/object to continue moving in that direction until i lift my finger.  This functionality does seem to work in ubuntu, but the cursor/object moves WAY too slowly to be useful.  Is there  a way to adjust the speed of the continued movement?

Thanks for your help!!
-Jack

---

### Post by ugm6hr on 2007-07-30
This is useful: [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Also:
```
man synaptics
```
This gives a full manual.

The settings you are looking for - I think - are:
> Option "EdgeMotionMinSpeed" "*x*"
Option "EdgeMotionMaxSpeed" "*x*"
Option "EdgeMotionUseAlways" "1"
Option "FastTaps" "1"
Option "LockedDrags" "1"

Where *x* is probably around *200* - but trial and error may be required (higher number=faster edge motion)!

You need to add these to xorg.conf (please backup original first):
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgbackup1.conf
gksudo gedit /etc/X11/xorg.conf
```

It goes beneath this bit:
>  Section "InputDevice"
   Driver      "synaptics"
   Identifier  "TouchPad"

Hope that helps.  Unfortunately, GSynaptics / QSynaptics just don't have the same level of control that the Windows Synaptic GUI allows - so it all needs to be done manually :(

---

### Post by Jack.Straw on 2007-07-30
Perfect, that's exactly the info i needed!  I have the locked-drag and edge motion speeds set perfectly to my liking now, thanks!  I haven't had a chance to play with the pad tap sensitivity, but you've provided all the information i should need.

Thanks for your time!!!  Much appreciated.
-Jack

---

### Post by iammeagain on 2007-12-20
Thanks for the link, solved my synaptics touchpad problems. The biggest one was that half of my touchpad thought it was supposed to scroll. A bit annoying. Thanks again.

---

