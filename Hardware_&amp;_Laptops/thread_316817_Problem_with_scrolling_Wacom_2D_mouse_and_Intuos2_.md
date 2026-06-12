---
title: "Problem with scrolling Wacom 2D mouse and Intuos2 talet"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by rquint on 2006-12-11
Sorry if this is a duplicate post, but I can't find my original thread.

I'm running Edgy (Linux Maria-Agnesi 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux) with the three wacom modules

wacom-kernel-source       1:0.7.2-0ubuntu7
wacom-tools               1:0.7.2-0ubuntu7
xserver-xorg-input-wacom  1:0.7.2-0ubuntu7

installed.

I have an Intous2 table for which everything works fine, except for scrolling with the 2D mouse.  Scrolling with the wheel is reversed from norma.  (BTW the PC is dual booting and the tablet and mouse work correctly, including scrolling, under WindowsXP.)  

I've tried changing my xorg.conf by changing the appropriate [?] section in xorg.conf to include options for Button4 and Button5--e.g.,

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option	   "Mode" "absolute"
    Option         "USB" "on"
    Option         "Button4" "5" 
    Option         "Button5" "4" 
EndSection

However this has no effect.  Including the option

    Option          "Button2" "4"

or

    Option          "Button2" "5"

DOES change the behaviour of a press of the scroll wheel to either scroll up or down as is expected.  I can also change the behaviours of Button1 and Button3 by including options, but nothing I've down with any Button numbered 4 or above in xorg.conf is reflected in the behaviour of my mouse.

I've been reluctant to remove wacom-tools and xserver-xorg-input-wacom because I am unsure of the effect of also removing xorg, xserver-org and xserver-org-input-all, as would be done by Synaptic.  Has anyone successfully done this without screwing up their X server installation and then installed the drivers from the linuxwacom project?

---

### Post by mscclr3 on 2006-12-25
I have the same problem w/ the wheel on the mouse that came with my graphire 4, did you ever solve this?

I tried to install the linuxwacom package but I couldn't find the deb once I had built the binary...

---

### Post by nigeltao on 2006-12-26
I filed a bug.
[https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226](https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226)

---

### Post by mscclr3 on 2006-12-27
Give a yell if any particular output is needed from a computer if you can't do it for whatever reason

---

