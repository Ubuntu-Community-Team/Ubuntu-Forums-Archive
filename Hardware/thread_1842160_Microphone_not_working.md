---
title: "Microphone not working"
date: 2011-09-10
forum: Hardware
---

### Post by xedth2 on 2011-09-10
So my speakers work fine and my webcam also works fine but for some reason my mic will not work at all.  I'm still kind of new to this system, Ubuntu 10.04 32 Bit, but if I were in a Windows environment I would say the driver isn't installed.  I'm running a Toshiba Satellite L670.  I want to use the mic with Skype but I've looked the Sound Preferences and the only option I see for "Choose a device for sound input:" is "Internal Audio Analog Stereo" and the input level meter never moves.  And the mute check box is not checked.

Thank you in advance

---

### Post by zhanglini on 2011-09-11
> **xedth2 said:**
> So my speakers work fine and my webcam also works fine but for some reason my mic will not work at all.  I'm still kind of new to this system, Ubuntu 10.04 32 Bit, but if I were in a Windows environment I would say the driver isn't installed.  I'm running a Toshiba Satellite L670.  I want to use the mic with Skype but I've looked the Sound Preferences and the only option I see for "Choose a device for sound input:" is "Internal Audio Analog Stereo" and the input level meter never moves.  And the mute check box is not checked.

Thank you in advance

If your kernel is not 2.6.38, you need to upgrade to that in Synaptic.  Just search for linux-image-2.6 and install linux-image-2.6.38-generic.
It solved my mic problem!

---

### Post by xedth2 on 2011-09-11
Alright don't understand how exactly that worked but it appears to have worked.  Now I shouldn't have an issue with Skype but if I do I'll post again.  Thanks a bunch!!

---

