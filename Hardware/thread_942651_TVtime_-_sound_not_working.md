---
title: "TVtime - sound not working"
date: 2008-10-09
forum: Hardware
---

### Post by Nanthiel on 2008-10-09
Hello there,

I have a Bt878 Video and a Bt878 Audio capture device (lspci shows the two of these) and tried to get TVtime to work. The video works, but the sound is only a silent noise.

The sound output of the card (physically) is connected to the Line-In of the onboard sound (which is an AC'97 Audio Controller).

Also, here is the output of:
```
$ dmesg | grep bt878
[   50.256979] tuner 2-0043: chip found @ 0x86 (bt878 #0 [sw])
[   50.258984] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   51.274042] bt878: AUDIO driver version 0.0.0 loaded
[   51.674457] bt878: Bt878 AUDIO function found (0).
[   51.674478] bt878_probe: card id=[0x1211bd], Unknown card.
[   51.674488] bt878: probe of 0000:05:07.1 failed with error -22
```
if it's any help.

What do you suggest I do?

- Matej

---

### Post by Nanthiel on 2008-10-14
Bump.

---

