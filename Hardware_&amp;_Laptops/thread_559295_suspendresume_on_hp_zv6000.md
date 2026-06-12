---
title: "suspend/resume on hp zv6000"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by scradock on 2007-09-25
I have an HP Pavilion zv6000 with ATI 200m video, using the fglrx driver. I cannot find out how to resume after suspend, either under Feisty or Gutsy.

In WinXP Home, all expected ways of putting the machine to sleep work; all expected ways of bringing it out of sleep work - touching the touch-pad, pressing a key, brief press of power button, Fn+f5. All bring me back to a log-in screen and resume windows with everything running except my wireless network connection, which has to restart.

In either Ubuntu version, the machine goes to sleep, but does not fully awaken. The fans start up, the lights come on, but the screen only goes to back-light stage and remains black. No X, no log-in screen.

The exception, in Feisty (with Compiz!) is that pressing the lid-close sensor blanks the screen but leaves a log-in password box visible; entering the password brings back the session I was in, including wireless connection.

Letting the machine sit inactive blanks the screen, and it wakes at a touch as expected on key-press or touch-pad touch, in Feisty or Gutsy. This is obviously a less severe suspend, probably only of the screen, leaving the X-server running but not displaying.

I've read many of the posts about this sort of problem; the issues seem to be very machine-specific, and I don't see anything about my model, or anything so severe as my problem. Most people are complaining about loss of what used to work; resume after suspend has never worked for me in Ubuntu, though it does in WinXP.

Any ideas? I've tried a few, but more would be welcome.

---

### Post by strawman on 2007-10-19
what works for me is omitting splash from the #defoptions line in /boot/grub/menu.lst

---

### Post by strawman on 2007-10-19
forgot to mention i'm using the open source driver but give it a try with fglrx

---

