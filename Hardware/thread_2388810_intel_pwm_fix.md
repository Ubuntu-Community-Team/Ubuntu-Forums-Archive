---
title: "intel pwm fix"
date: 2018-04-07
forum: Hardware
---

### Post by kao on 2018-04-07
Hi, 
I am trying to fix awful PWM on my mi air 12.5 that is based on i915 video (change PWM freq from 200Hz to 2000Hz)
There [http://devbraindom.blogspot.com/2013/03/eliminate-led-screen-flicker-with-intel.html](http://devbraindom.blogspot.com/2013/03/eliminate-led-screen-flicker-with-intel.html)  I found advice that works fine except one caveat critical for me:
almost unadjastable brightness level

Why is that?
There is /sys/class/backlight/intel_backlight/max_brightness parameter that equals to initial higher 4-bytes value. And changing brightness is performed by steps that are calculated based on that value. But after changing frequency to higher value our period drastically decreases.
E.g.
Old freq = 200Hz (period = 937, cycle 350, max bright = 937)
New freq = 2000Hz (period = 94, cycle 35, actual max bright = 94)
Step of brightness change is 1%. It is ~9 in period measure. It is not changed while intel_gpu write operation.
In ideal case, I can change brightness under new frequency by step ~1.
But in our real case, I still change it with step ~9

I assume that mentioned issue could be resolved by changing /sys/class/backlight/intel_backlight/max_brightness. But I cannot change it even under root account.

I have tried to change VBT dump from /sys/kernel/debug/drm/{number}/i915_vbt (PWM frequencies) and load it via kernel param i915.vbt_firmware.
It works fine and I can see that dump has new PWM values.

However it doesn't lead to resolving of the issue. PWM is still not fixed. 
I can see that opregion dump (i915_opregion) that should incapsulate VBT has the initial values while VBT dump (i915_vbt) has fixed values.

May be someone advance more than me. Please advise
Thank you

---

### Post by ajgreeny on 2018-04-07
Can I please check that you're not still using Ubuntu Gutsy Gibbon as your signature suggests.
I suspect that is just an old signature that you have failed to update but it is important for us to know as Gutsy Gibbon lost support a very long time ago.

---

### Post by kao on 2018-04-08
Changed signature. Sorry.

---

