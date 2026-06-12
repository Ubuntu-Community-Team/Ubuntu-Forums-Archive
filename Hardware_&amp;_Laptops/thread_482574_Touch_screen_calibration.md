---
title: "Touch screen calibration"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by mortalic on 2007-06-23
Does anyone know of a method to calibrate a touch screen in linux?

I have an older fujitsu lifebook B series.  The touchscreen works fine but it's out of calibration.

I was thinking of installing vmware and windows just to see if the windows drivers would affect it in a vm.  Anyone have a good idea?

---

### Post by deculpep on 2007-07-05
I just purchased a Fujitsu Lifebook B-2562.  Touch screen works, but it is badly miscalibrated.  Can anybody help us out?  Its a 10.4 inch touch screen (ie you can use fingers, pen, anything, not a digitizer pen like the newer tablets) 700MHz pentium IIIM.  Running single boot of Xubuntu Feisty.

Hopefully relavent dmesg output:

[   41.988000] input: LBPS/2 Fujitsu Lifebook TouchScreen as /class/input/input2

Once I get the screen going right, this little thing will be a powerhouse for notes in class, but I need some help!
This post is all I've been able to turn up, any assistance would be greatly appreciated and I'm provide any infomation to get this worked out.

---

### Post by geraldm on 2007-07-06
In the linux kernel source, there is some documentation in 
Documentation/usb/mtouchusb.txt.  That device provides its data
in raw form, and would need to be translated (or calibrated?).
Some development remains on that one, but there are some
references in it.
Gerald

---

### Post by DagMan on 2007-07-06
There are gui tools for both ubuntu and kubuntu.  I think in both cases they don't work unless you add a line to the xorg.cong file in /etc/X11

Mine looks like this
```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig" "on"
EndSection
```
and the important thing to allow configuration is this line
**    Option         "SHMConfig" "on"**

If the gui tools, I think it's called gsynaptics or something so shouldn't be hard to find in the package manager.. if they don't work then it can be adjusted adding the settings directly to the xorg.conf file in this same section above that I've posted.  I don't know how specifically but had it done that way on another computer a while back and had found the instructions in the tips and tricks section of the forum.


Edit:  Okay I see now that I saw touchpad instead of the wanted touchscreen.  I'll leave it up in case others pass through in a search wanting to configure their laptop touchpad mouse pointers though.  Sorry I couldn't help with the topic.

---

### Post by deculpep on 2007-07-06
Thanks for the responses guys!

I came across something known as evtouch [http://stz-softwaretechnik.com/~ke/touchscreen/lifebook-2.6.html](http://stz-softwaretechnik.com/~ke/touchscreen/lifebook-2.6.html)

It is my understanding that this is now built into the kernel I'm using.  (Sorry at work right now, and I can't get the exact version, but it is the latest available in the repo's)

I would think that the calibration would have something to do with the values in my xorg.conf, but the values I entered following the configuration instructions are meaningless to me.  I'll post my xorg.conf in a couple hours and play around with changing the values.

I also saw that there is a xserver-xorg-input-void package in the Ubuntu repos, I'll give that a try as well as the evtouch instructions call for it.

EDIT: looks like our friends with Samsung Q1's in this forum are having similar calibration issues with their touch screens.  [http://ubuntuforums.org/showthread.php?t=419235](http://ubuntuforums.org/showthread.php?t=419235) Since both of us are using evtouch, I'll give that a try first.

---

