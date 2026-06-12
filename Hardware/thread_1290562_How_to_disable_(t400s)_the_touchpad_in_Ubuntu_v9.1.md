---
title: "How to disable (t400s) the touchpad in Ubuntu v9.10 beta?"
date: 2009-10-13
forum: Hardware
---

### Post by hurryon on 2009-10-13
Hi, all.

I've been working with t400s (Lenovo). Ubuntu v9.04 does not have any problem with my laptop, but Ubuntu v9.10 beta has a problem. One thing I found is that I cannot disable the touchpad.

The function key for enabling and disabling the touchpad ( Fn + F8 ) does not work. Note that other function keys are well working.

Anyone know how to solve it? I just disable the touchpad and then want to use only the trackpoint.

---

### Post by patspam on 2010-01-24
Have you retried in v9.10 stable? Works like a charm for me.

---

### Post by patspam on 2010-01-25
One quirk, I just discovered that if you have "Disable touchpad while typing" checked in System > Preferences > Mouse, the touch-pad automatically turns on again as soon as you type something (I guess there's a bug in the code that blindly re-enables it after typing without checking if it was disabled to begin with).

This happens regardless of whether you disable the touchpad via Fn + F8 or the "synclient TouchpadOff=1" command.

If you uncheck "Disable touchpad while typing" it seems to work ok.

Just had a look and there's already a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/501990](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/501990)

---

