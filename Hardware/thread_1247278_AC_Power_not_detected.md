---
title: "AC Power not detected"
date: 2009-08-22
forum: Hardware
---

### Post by Zatara214 on 2009-08-22
I have the same issue as the guys in this thread:

[http://www.nvnews.net/vbulletin/showthread.php?p=2050621](http://www.nvnews.net/vbulletin/showthread.php?p=2050621)

nvidia-settings (and Ubuntu) constantly detects that I'm in battery mode, even though I almost never am.  This is causing issues with Nvidia's powermizer, it's underclocking my card and crippling my performance with Compiz (and other stuff)  Is there any way that I can get Ubuntu to detect properly that I am on AC power?

I have the same laptop as one of the guys in the thread above, a Sager NP8660 (Clevo MT860U) with a 9800m GT.  My clocks should be at 500/799, but are constantly underclocked to 275/301.  Enabling Coolbits does not work, as it will only allow me to underclock my card further while in battery mode.

Powermizer has four performance levels for me, with 0 being the lowest (200/100) and 4 being the highest (500/799).  On battery mode, I cannot get above level 1 (275/301), even when running a 3D application (such as glxgears).

Anyone have any ideas?

---

### Post by Zatara214 on 2009-08-27
Bump for good justice.  This is one of those issues that I really can't go on without solving.

---

### Post by eival on 2009-09-04
i have the same issue but my card actually says im on AC power, but still uses the adaptive clocking....

i read that upgrading to the latest driver 190.xxxx (which is still beta) fixed this issue but i still dont see any option to disable the adaptive clocking and set the performance level manually. so its still fluctuating and runnin hot when i try to run apps. and it tries to get back to level 0 as fast as possible even when im still running hot an the internal temp is 90+degrees.

ive seen some scripts around the net that can manipulate the fan to run at a high speed or make it run at max performance all the time, but i really dont want to use work-arounds, id like nvidia and ubuntu to fix this legitimately.

---

### Post by Zatara214 on 2009-09-09
Well my issue is a bit more complicated.  It's described in detail in the bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/412499](https://bugs.launchpad.net/ubuntu/+bug/412499)

It seems to be an issue with ACPI.  I currently have the latest 190.32 drivers installed from the VDPAU PPA.  Unfortunately, because my laptop thinks that I'm constanty on battery, even setting Powermizer to 'Maximum Performance' mode only allows me to get to 275/301 clocks.  I need a way to force the laptop to think that I'm on AC power.

Even just doing this for the Nvidia driver would be fine.  It's obviously detecting my battery, so there must be a way to stop it from doing that, right?  Anyone have any ideas on how to do this?

---

### Post by eival on 2009-09-19
try this out

[http://aldeby.org/blog/index.php/enable-nvidia-coolbits-frequency-tuner.html](http://aldeby.org/blog/index.php/enable-nvidia-coolbits-frequency-tuner.html)

---

