---
title: "Logitech mouse"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by Milambar on 2007-02-14
I'm trying to get the forwards/backwards buttons on my Logitech mouse working in firefox.

> 
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
        # Added to get forward and back buttons working.
        Option          "Buttons"               "7"
        Option          "ButtonMapping"         "1 2 3 6 7"
EndSection


The mouse works, but the forwards/back buttons don't, even having restarted X several times. No, I won't do a complete reboot, this is ubuntu, not windows. That config change and restarting X has always worked for me in the past, on a multitude of distributions.

I am aware of the other "posts" suggesting that you edit .xbindkeysrc, chant at the moon on the 4th sunday of the blue moon etc. 

I know that a change in xorg.conf is all thats needed, at least, all thats needed in debian, mandriva, redhat.... etc. So, what am I missing here?

Many thanks

Milambar

---

### Post by daou on 2007-02-14
You probably need to use the evdev driver to get all the buttons working. You might want to look at the whole [Logitech Mice howto]("http://www.ubuntuforums.org/showthread.php?t=219894"). Or if you have an MX or VX Revolution, [look here]("http://www.ubuntuforums.org/showthread.php?t=277388").

---

### Post by Milambar on 2007-02-14
I don't want all the buttons working, just the forwards and backwards buttons.

That howto is the post I said Im aware of, and also totally un-necesarry in any linux distribution, except it seems, ubuntu. The forwards button is usually mapped as mouse button 6 and backwards is usually mapped as 7, by default.

I don't care about the horizontal scrolling, or the zoom in/zoom out, I never ever use them.

The forwards button currently acts as if its a second RMB, so the buttons are being seen by the system, its not as if they are invisible.

Adding more packages, and system overhead is not a tenable solution for me, its running slow enough as it is, I only have a 500mhz laptop with 128Mb ram.

Given that I can get the forwards/backwards buttons working under any other distribution without the addition of evdev etc, I assume its also possible under ubuntu, unless the developers have gone out of their way to do things differently from any other distribution.

---

### Post by daou on 2007-02-14
The evdev module is quite small and already comes with the distro. There isn't much overhead involved in using it. And if xev doesn't register any events from the buttons you want functions for, I would suspect that it won't be easy (possible?) to bind them.

---

### Post by daou on 2007-02-14
If, however, xev recognizes the forwards and backwards buttons as some other number (for example 9 & 10 instead of 6 & 7), you can use a simple xmodmap command switch their numbers.

---

### Post by Milambar on 2007-02-14
Well, to satisfy the pundits, I installed evdev as per that tutorial..

The system was hugely slow to reboot, suggesting that the module adds more overhead than you  believe.

Xorg refused to restart..

> 
simon@ubuntu:~$ tail /var/log/Xorg.0.log
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb" };
    xkb_geometry             { include "pc(pc105)" };
(II) evdev brain: Rescanning devices (2).
No core pointer

Fatal server error:
failed to initialize core devices


> 
Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "evdev"
       Option          "CorePointer"
       Option          "Device"        "/dev/input/event6" 
EndSection

#Section "InputDevice"
#        Identifier      "Configured Mouse"
#       Driver          "mouse"
#        Option          "CorePointer"
#        Option          "Device"                "/dev/input/mice"
#        Option          "Protocol"              "ImPS/2"
#        Option          "Emulate3Buttons"       "true"
#        Option          "ZAxisMapping"          "4 5"
        # Added to get forward and back buttons working.
#        Option          "Buttons"               "10"
#        Option          "ButtonMapping"         "1 2 3 6 7 4 5"
#EndSection


> 
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Reciever", NAME="input/event6"


Any other suggestions?

---

