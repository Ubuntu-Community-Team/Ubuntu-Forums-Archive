---
title: "Audio Turns off when volume is adjusted (Intel HDA)"
date: 2007-12-25
forum: Hardware &amp; Laptops
---

### Post by keyo on 2007-12-25
I have a problem where my audio works fine when I boot up (ASUS z99he laptop) but when the audio is adjusted the sound stops. I have messed around with the volume controls and nothing gets it working again.

The output of 'lspci' for the audio chip
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

Thanks in advance for any help.

---

### Post by ItsManaged on 2007-12-30
I'm having the same problem using an Asus A8Fm series notebook. Sound works fine, then attempt to adjust volume control and sound is gone until next reboot, Restarting alsa does not fix it - it must be rebooted. My Compaq X1400 works fine and just about every other machine I've installed gutsy on (quite a few). I haven't been able to resolve it through the various approaches suggested via a google search..

I'm beginning to wonder if this has anything to do with the new VISTA DRM spec? (Just a stab in the dark - given I haven't been able to solve it through software).

You may want to try the following URL: 
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Cheers, and happy new year!

---

