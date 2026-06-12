---
title: "Microphone doesn't work on Dell XPS M1330"
date: 2009-10-12
forum: Hardware
---

### Post by ENSORS_ORAC on 2009-10-12
I've reviewed the existing posts on microphone problems. I didn't see a strong match on laptop model or kernel version so I am posting a new thread.  



1) Installed the latest alsa-utils package and issued:

sudo /etc/init.d/alsa-utils restart

2a) [IMG]file:///tmp/moz-screenshot.jpg[/IMG]Volume control/ preferences/ select tracks to be visible [device = HDA intel (ALSA mixer)]: Master, Headphone, PCM, Front and Capture. There is no microphone or booster option. 

b) Recording tab: microphone symbol is not crossed out, volume =max

3) Applications/Sound & Video/Sound recorder: no sound during playback (speakers work)


Thanks




Further details:

cat /proc/version
Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

