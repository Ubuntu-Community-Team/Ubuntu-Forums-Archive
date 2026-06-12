---
title: "SigmaTel ID 7698 - no audio"
date: 2008-07-30
forum: Hardware
---

### Post by michaelwigle on 2008-07-30
I have a Medion Akoya E5312 laptop from Aldi. The wireless took some work to get going but I have had no luck on the audio. Here is some hardware details:

michael@Wigle-LT-Linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

michael@Wigle-LT-Linux:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel ID 7698

There are plenty of posts about Intel HD problems but not ATI problems. The processor is an AMD Turion 64X2. If anyone has any ideas I would greatly appreciate it or I may have to return it.

---

