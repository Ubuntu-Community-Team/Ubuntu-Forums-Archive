---
title: "Thinkpad display blank"
date: 2009-08-30
forum: Hardware
---

### Post by bigirontx on 2009-08-30
I have a ThinkPad T42. Has been working fine (both Ubuntu Jaunty Jackalope and Windows XP). But I now get nothing on the screen - not even the BIOS splash screen.

This happened after I got hung in a non-privileged user. I had tried to use two monitors (the built in, and a HDTV (VGA interface). After trying to set as independent monitors (unchecking "mirror screens"), all the stuff that runs across the top disappeared. There was nothing left on the screen except the orange background. I couldn't do anything - not even log off. A left click on the screen brought up a menu that included shutdown, hibernate, suspend (but not logoff). It wouldn't let me shutdown (not enough privilege).

So I powered down by pushing and holding the power button. (At least I think it powered down - all the lights went off except the one that shows you are connected to AC - and the cresent moon that shows suspend state was off.)

Now when I power on, the ThinkPad's screen stays totally blank. I don't even get the BIOS splash screen. I do get disk activity, but never anything on the screen. 

Attaching the HDTV back up doesn't help. Also tried another monitor on a DVI interface (on my docking station). Nothing displayed on any screen.

Any ideas? Is there a "default monitor" BIOS setting that Ubuntu might have changed. If so, how can I change it given that I never get anything on the laptop screen - or any other monitor?

(I tried removing the battery and letting it sit for a couple of hours - but that didn't help.)

Rich

---

### Post by bigirontx on 2009-09-05
> **bigirontx said:**
> I have a ThinkPad T42. Has been working fine (both Ubuntu Jaunty Jackalope and Windows XP). But I now get nothing on the screen - not even the BIOS splash screen.

This happened after I got hung in a non-privileged user. I had tried to use two monitors (the built in, and a HDTV (VGA interface). After trying to set as independent monitors (unchecking "mirror screens"), all the stuff that runs across the top disappeared. There was nothing left on the screen except the orange background. I couldn't do anything - not even log off. A left click on the screen brought up a menu that included shutdown, hibernate, suspend (but not logoff). It wouldn't let me shutdown (not enough privilege).

So I powered down by pushing and holding the power button. (At least I think it powered down - all the lights went off except the one that shows you are connected to AC - and the cresent moon that shows suspend state was off.)

Now when I power on, the ThinkPad's screen stays totally blank. I don't even get the BIOS splash screen. I do get disk activity, but never anything on the screen. 

Attaching the HDTV back up doesn't help. Also tried another monitor on a DVI interface (on my docking station). Nothing displayed on any screen.

Any ideas? Is there a "default monitor" BIOS setting that Ubuntu might have changed. If so, how can I change it given that I never get anything on the laptop screen - or any other monitor?

(I tried removing the battery and letting it sit for a couple of hours - but that didn't help.)

Rich
This is resolved. In addition to removing the main battery and, of course, unplugging the computer, I had to remove the "Backup battery", i.e., the little coin sized battery that keeps the CMOS/BIOS memory when there is no power. This apparently reset the BIOS back to the factory defaults. Once that was done, and put everything back together, I got the BIOS splash screen when I powered on and was able to get into the BIOS and set reasonable settings. Then everything booted ok.

This leads me to believe that Ubuntu messes with the BIOS settings (at least the BIOS display settings when running with multiple monitors) and that my powering off the machine without kept Ubuntu to restore those settings.

Any comments? Anyone know if Ubuntu changes BIOS settings?

Rich

---

