---
title: "[Dell Latitude E6400] Touchpad issues"
date: 2008-11-08
forum: Hardware
---

### Post by Sir Galahad on 2008-11-08
Hello,

I'm using a Latitude E6400 and Ubuntu is working fine so far. Unfortunately I'm experiencing some problems with the touchpad. I don't have a "InputDevice" section in my xorg.conf so the touchpad obviously has not been recognized by Xorg. It's working though (much to my annoyance (I loathe touchpads)) except for the scrolling feature, and I can't turn it off in my xorg.conf for obvious reasons.
**However**, when using Gnome (which I also loathe), I am able to disable it by System->Preferences->Mouse->Touchpad. Even the scrolling feature works with Gnome. What does Gnome do in order to disable it (I figure it does not make use of gsynaptics)?

Any suggestions will be greatly appreciated.

Regards,
Sir Galahad.

---

### Post by wgrant on 2008-11-08
Configuration of input devices in xorg.conf is now very much deprecated and somewhat broken; the X server detects devices from HAL. See [the X input device configuration documentation](https://wiki.ubuntu.com/X/Config/Input) for details on configuring things in Ubuntu 8.10.

---

### Post by softtower on 2008-11-09
Sir Galahad, have you figured out how to adjust touchpad sensitivity/speed? I have an identical laptop and the slowness of the touchpad is driving me nuts. I've been playing with xinput last night but was unable to find how to adjust speed...

---

### Post by wgrant on 2008-11-09
Speed is a floating-point number, so can't currently be exposed through xinput (float representations differ between architectures, so they can't be used straight in the X protocol). You should configure such things through HAL fdi files for now.

---

