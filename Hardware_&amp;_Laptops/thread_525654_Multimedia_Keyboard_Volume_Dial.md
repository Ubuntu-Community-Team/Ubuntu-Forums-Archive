---
title: "Multimedia Keyboard Volume Dial"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by scuba_steve on 2007-08-14
Hey, I have an HP Multimedia Keyboard model 6511-SU.  I have been able to get most of the extra buttons working using the normal xmodmap methods, but I still cannot get the volume dial working.

I've had the keyboard apart, and I noticed that the volume dial seems to be an independent device from the keyboard itself - it's attached to a small board on one of the keyboard's usb ports, not on the keyboard circutry itself.

So sure enough, i found and ran Gizmo Deamon in debug mode and it gave me the following output for the dial:
> 
onEvent: Standard -- /dev/input/event4 | [EV_ABS] c: 0x20 Val: 0x1
onEvent: Standard -- /dev/input/event4 | [EV_ABS] c: 0x20 Val: -0x1

For Volume up & Voume Down respectively.  All other keyboard events are /dev/input/event3.   Now, gizmod seems like a nice enough program but for simplicity I would rather just set up a driver for /dev/input/event4 in my X11 and assign values to the output using the standard xmodmap method, or something similar.

I actually don't really care that much how I do it, I just want to get my volume dial working!

So does anybody know if there's a driver out there for a simple usb dial that gives the output specified above?  How hard would it be to write a driver myself?

Any help would be greatly appreciated!  Also, once it's working I'd like to use it for Master Front Right only.....

---

