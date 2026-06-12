---
title: "Another 'No Sound' question"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by larrinh on 2009-03-15
I just installed ubuntu 8.10 AMD64 and have the following problem. NO SOUND. I have an XFX GeForce 8200 modo with NVidia 8200 video chipset and Realtek ALC1200 audio chipset. I can tell you that I did have sound after I first installed but when I updated the video to the NVidia 180 drivers the sound stopped. 

Prior to update:

larrin@edgar:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 

larrin@edgar:~$ lspci
...
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
...

After update:

larrin@edgar:~$ aplay -l
aplay: device_list:207: no soundcards found...

larrin@edgar:~$ lspci
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

I need to keep the video drivers and not roll them back because without them my monitor looked like crap. Any suggestions? I thought about getting the newest Realtek drivers and recompiling the ALSA package to include them but I would be in way over my head without a step by step guide. This is, after all, my first week using Linux.

Thanks for any help,
svbhvman

---

