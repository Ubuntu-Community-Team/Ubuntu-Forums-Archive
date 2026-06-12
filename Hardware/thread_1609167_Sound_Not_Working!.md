---
title: "Sound Not Working!"
date: 2010-10-30
forum: Hardware
---

### Post by viral88 on 2010-10-30
Hi,

I just installed Ubuntu 10.04 on my HP G62-361TX laptop which has a 1 GB ATI Mobility Series HD 5470 graphics card. However, the sound doesn't seem to be working! I tried running both media files and videos from Youtube, but both of them don't work

Typing aplay -l in the terminal gives me the following message:

ubuntu@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ubuntu@ubuntu:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

Can someone please help me out here...

---

### Post by fallenshadow on 2010-10-30
You would be better off using Ubuntu 10.10 than 10.04. I had a really bad experience with 10.04 regarding PulseAudio (the sound support package)

10.10 is better by far for audio/sound! 10.10 is also better overall!

---

