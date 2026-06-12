---
title: "Can't come back from Suspend"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by dotpage on 2007-05-01
I have an IBM ThinkPad Z61m running 7.04 that won't come back from suspend w/o a reset. I tried to find an answer to the problem but could not find it... The sleep LED keeps blinking after going into suspend.

I followed the instructions @ [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T60) but had no luck.

Anybody has a clue why this happens?

---

### Post by SoggyCornflake on 2007-05-02
> **dotpage said:**
> I have an IBM ThinkPad Z61m running 7.04 that won't come back from suspend w/o a reset. I tried to find an answer to the problem but could not find it... The sleep LED keeps blinking after going into suspend.

I am familiar with several different laptops. but have not actually ever used an IBM Thinkpad.  What does a flashing LED mean when speaking about a Thinkpad?  For a lot of laptops the power LED flashing when the laptop is suspended.   This sound like a lock up on resume rather than locking up on suspending -  (Perhaps that may be useful for somebody diagnosing the problem.)  

This first thing I would do is check the BIOS version and if there is a newer BIOS, follow IBM's instructions for upgrading the BIOS.  ( A lot of suspend / resume issues are BIOS related.)

Other suspend/resume issues are related to device drivers/kernel modules.  Quite often laptops lockup in suspend/resume because a device was not correctly put into suspend mode.  Disable as many devices as you can prior to suspending to see if it still locks up.  If the laptop doesn't lockup on resume, then enable one of the devices and resuspend/ resume.  Keep doing that until the laptop locks up.  (The last device you re-enabled is probably the device causing the problem.)

You can get and idea what devices are causing the problem by typing the following commands in a console window: ```
lspci
lsusb
```

---

### Post by dotpage on 2007-05-02
BIOS is the latest, and turning off other resources/hardware to fix a problem is not a fix...

---

