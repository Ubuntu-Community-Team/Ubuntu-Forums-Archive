---
title: "No headphone output on Sony laptop"
date: 2008-10-14
forum: Hardware
---

### Post by Amorget on 2008-10-14
Hi, I am having a problem with my Sony VGN-AR670.  I have no headphone output.

Output of aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and  lspci | grep -i audio

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

I have tried both ALSA and Pulse Audio, but they don't have any affect on anything.  Also, my HDMI audio output doesn't work, either, if that makes a difference.

Any ideas?

Douglas

---

### Post by Amorget on 2008-10-17
Any thoughts on this out there?

---

