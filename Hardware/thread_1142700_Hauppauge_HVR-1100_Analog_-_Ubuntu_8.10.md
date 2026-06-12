---
title: "Hauppauge HVR-1100 Analog - Ubuntu 8.10"
date: 2009-04-29
forum: Hardware
---

### Post by pavelp on 2009-04-29
I have Hauppauge HVR-1100 TV card installed, using Ubuntu 8.10 (all updates to date of this post)
I want to use Analog part of this Hybrid TV Card, all seems to work well, all drivers loaded. Using TVTIME and MythTV. Problem is, that analog tuner doesn't work. When i start TVTIME i see video, but there is only noise. When i change channel (frequency) the noise changes, so apparently there is some tuning going on but it tunes to wrong frequencies.

I was trying to figure out why this is happening, after some experiments it looked like it doesn't like to have both analog and DVB drivers loaded together,  so i tried to unload DVB related drivers and it started to work correctly (i was able to tune to channels and even scan for them which was not possible to do before). So i decided to blacklist these modules and rebooted. After reboot, the DVB part was not loaded but tuning didn't  work. So i tried to unload rest of the drivers (cx88xx and cx8800 is used for this card as i understand looking on dmesg) and loading it back, and nothing still the same. After some trying loading and unloading modules for this card (cx88xx, cx8800, tuner, tuner_simple) i got it back working but don't know what exactly did it.

To now, i didn't find reproducible way to make it work. Please can somebody help?

Thank you

---

