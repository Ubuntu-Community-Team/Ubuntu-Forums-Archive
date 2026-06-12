---
title: "Can't permanently disable tapping on my touchpad"
date: 2009-11-22
forum: Hardware
---

### Post by Gurduloo on 2009-11-22
I have a Lenovo laptop with a Synaptics brand touchpad.  I need the tap-to-click disabled.  In previous versions, it was easy, I go to System-Administration-Touchpad and disable tapping.  Now with 9.10 I can still do that, and it works, but when I reboot, the tapping is usually enabled again.  What am I doing wrong?

---

### Post by mgol on 2009-11-23
System -> Preferences -> Mouse -> Touchpad -> uncheck "Enable mouse clicks with touchpad".

---

### Post by jwmuelle on 2009-11-23
or, if you want to disable all touchpad functions, disable it in the bios.

---

### Post by Gurduloo on 2009-11-23
> **mgol said:**
> System -> Preferences -> Mouse -> Touchpad -> uncheck "Enable mouse clicks with touchpad".

Ok, is that different than going to System -> Preferences -> Touchpad -> uncheck "Enable Tapping" ?
Kind of weird that it appears in two different places.

---

### Post by mgol on 2009-11-24
> **Gurduloo said:**
> Ok, is that different than going to System -> Preferences -> Touchpad -> uncheck "Enable Tapping" ?
Kind of weird that it appears in two different places.
Hmm... I don't see this one at all. Did You upgrade from Jaunty?

---

### Post by linds2009 on 2009-11-24
Download a touchpad control software

---

### Post by Gurduloo on 2009-11-24
> **mgol said:**
> Hmm... I don't see this one at all. Did You upgrade from Jaunty?

Yes, I upgraded from Jaunty.  "System -> Preferences -> Touchpad" might be some leftover package.  I believe I had to install GSynaptics at some point (maybe back as far as 8.04) to solve this very same problem before.  I tried your way and so far so good, but I'll wait a few days before declaring this solved.

---

### Post by Gurduloo on 2009-11-30
Just to update - I've removed Gsynaptics from my install now and everything's fine.  Disabling the tapping on Preferences -> Mouse -> Touchpad was the correct way to go, and uninstalling Gsynaptics removed extra item in my preferences menu that was confusing me.

---

### Post by cyqotiq on 2009-12-01
I'm having a similar problem on my Dell Studio 17 w/Synaptic Touchpad.  I have installed the *Touchpad Preferences* application using the Ubuntu Software Centre.  Imagine my excitement to see right there on the front page of this program a check-box labelled "Enable Touchpad".  I cleared the check-box and went about my merry way.  Usually within 1 minute, the touch-pad was re-enabled, scrolling wildly and causing my browser to jump back a page or three as my palm glides across the touch-pad surface.

> **jwmuelle said:**
> or, if you want to disable all touchpad functions, disable it in the bios.
This isn't a viable option for me because I don't always have my USB wireless mouse handy.

I began to get curious and started thinking about what was happening.  I noticed fairly quickly that my touch-pad was being re-enabled while I was typing.  So I went to System/Preferences/Mouse and reset the "Disable Touchpad While Typing" option to "Off" (i.e. I cleared the check-box).  I then went back to the System/Preferences/Touchpad application and cleared the "Enable Touchpad" check-box.

I've been using the computer in this state for about 30 minutes now with no touch-pad activity.

I'm guessing that with the "Disable Touchpad While Typing" option checked in the System/Preferences/Mouse application, it was re-enabling the touch-pad when I paused my typing - despite my turning the touch-pad off in System/Preferences/Touchpad.  Now, with the "Disable While Typing" option not set, the touch-pad settings from System/Preferences/Touchpad are sticking.

Hope this helps!

PS - I'm currently laid-up in the hospital.  I've just had surgery on a broken leg, so I'm quite loopy on medication.  I apologise for any "rambling" I may have done in this post.

---

