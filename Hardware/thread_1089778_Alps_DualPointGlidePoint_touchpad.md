---
title: "Alps DualPoint/GlidePoint touchpad"
date: 2009-03-07
forum: Hardware
---

### Post by gehzumteufel on 2009-03-07
I have been searching, and searching and not really found anything.

Is there a way to fully disable the touchpad and the associated click buttons but leave the stick with its associated click buttons enabled?

Thanks in advance! :)

edit//I am using kubuntu 8.10 and the xorg.conf has almost nothing there. Everything there is pertaining to monitor config.

---

### Post by ananaza on 2009-03-13
I've been trying to do the same. I'm running 64 bit intrepid on Dell Latitude E4300. In principle it should be possible to disable the touchpad from the mouse preferences but the touchpad tab is not always there. This seems to be related to problems in the psmouse kernel module. I've applied the patch describe in:

[http://lkml.org/lkml/2008/12/8/182](http://lkml.org/lkml/2008/12/8/182)

which improves things but I still get funny behavior. If I e.g. slide two fingers towards each other on the touchpad, the mouse pointer jumps (usually to top left corner). Also, something is missing button presses/releases somewhere. Occasionally a button press is simply not recognized. Sometimes a release gets recognized only after slightly moving the mouse pointer with the pointing stick.

Bugs worth looking into are at least:

[https://bugs.launchpad.net/ubuntu/+bug/296610](https://bugs.launchpad.net/ubuntu/+bug/296610)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/292047](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/292047)

---

### Post by dorseye on 2009-05-03
Bump!

I have a SL300, trying to do the same thing (if I read your post correctly.) I want to disable the alps touchpad and its buttons, but leave the "eraser" mouse and the 3 buttons below the KB working.

---

