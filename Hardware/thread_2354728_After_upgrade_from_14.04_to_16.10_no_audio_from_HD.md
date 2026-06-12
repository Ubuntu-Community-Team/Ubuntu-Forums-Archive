---
title: "After upgrade from 14.04 to 16.10 no audio from HDMI"
date: 2017-03-05
forum: Hardware
---

### Post by grahamsaulnier on 2017-03-05
I just upgraded from 14.04 to 16.10 and upon plugging back into my TV via HDMI I am not getting any audio. If I got into my Pulse Volume Control settings one of the built in audio devices is showing that sound should be playing. If I go under Configuration all of my Digital Stereo/Surround (HDMI) Output are marked as '(unplugged)'. 

Thanks for any help please let me know what other information you need.

---

### Post by opsusec on 2017-03-06
I had this issue in SuSE, where I had to mix two drivers (alsa / pavucontrol) in order to manage it. I'd say add an argument to the directory making one driver fall back to the other upon PCI enumeration / connection // disconnection. That's the only logical solution i can think of my friend.

---

