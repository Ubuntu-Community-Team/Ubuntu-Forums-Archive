---
title: "Disoriented mouse with dual-monitor"
date: 2010-10-21
forum: Hardware
---

### Post by DasherDooDad on 2010-10-21
My laptop gets into a state where, when I click on the mouse buttons, it thinks that it's pointing somewhere that it's not. When I click on the mouse buttons, usually nothing happens, although sometimes the right button causes a menu to pop up somewhere else on the screens.
I have to go find the window where I was working before, click on the right mouse button to pull up a menu, then go to where I want to work, click on the right mouse button to pull up a menu, and then I can work on that window.
Also, selecting with the right mouse button is not implicitly copying, and the middle mouse button does not paste.
I have no idea what's causing this. It happens pretty frequently when I work in dual-monitor mode. Things work fine when I log in, then this problem kicks in after awhile. I can clear it by rebooting. I've seen it happen with single-monitor mode as well, just not as often.
I haven't seen any posts by anyone else having this problem.
I'm running Ubuntu 10.04.1 LTS ("lucid") on a Dell Latitude E6500, with BIOS A23.

---

### Post by DasherDooDad on 2010-10-21
There was an earlier post
[http://ubuntuforums.org/showthread.php?t=1262224](http://ubuntuforums.org/showthread.php?t=1262224)
about the same problem. Rearranging my USB plugs isn't helping me, and I have the same problem with the mouse built into my laptop.

---

### Post by DasherDooDad on 2010-10-21
I cross-posted the issue to the Dell community website:

[http://en.community.dell.com/support-forums/software-os/f/3525/p/19350738/19766183.aspx#19766183](http://en.community.dell.com/support-forums/software-os/f/3525/p/19350738/19766183.aspx#19766183)

---

### Post by DasherDooDad on 2011-03-26
I see the problem standalone when I have wireless enabled.
It looks like there is a bad variable in the kernel somewhere that is affected by the drivers.

---

### Post by DasherDooDad on 2011-05-25
So far it looks like I can prevent the problem by killing the Touchpad:
    xinput set-prop "AlpsPS/2 ALPS DualPoint TouchPad" "Device Enabled" 0
    xinput set-prop "PS/2 ALPS DualPoint TouchPad" "Device Enabled" 0
Which one I use depends on whether the laptop is docked or not.
The mouse stays oriented 100% after that.
I believe the root cause is that the Synaptics driver does not manage the Alps touchpad on the Dell Latitude E6500.

---

