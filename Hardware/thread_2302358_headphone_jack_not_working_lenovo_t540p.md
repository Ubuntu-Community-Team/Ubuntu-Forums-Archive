---
title: "headphone jack not working lenovo t540p"
date: 2015-11-09
forum: Hardware
---

### Post by davidkpanda on 2015-11-09
problem:
headphone sound not working; 
front speakers work;
headphone works with static after suspend

setup:
fresh install 15.10 server
alsa-utils installed
lenovo t540p
preferred device is card 1 (HDMI being card 0)

Any help I can get would be great.  Thanks.

Edit:  It seems that starting the laptop with headphone plugged-in causes this problem.  Starting the laptop without a headphone works fine.  Also, instead of changing /etc/share/alsa/alsa.conf directly, configuring ~/.asoundrc as below seems to help; starting the laptop with headphone still causes the problem, though.  Any help is appreciated.

```

$ cat .asoundrc
pcm.!default { 
       type hw 
          card 1 
} 


ctl.!default { 
       type hw 
          card 1 
} 


 $ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3232 Analog [ALC3232 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0         

```

---

### Post by davidkpanda on 2015-11-10
Just in case if anyone has a similar problem,

I fixed the problem by moving ~/.asoundrc to /etc/asound.conf .  I am not sure why this works instead of the original solution.

---

