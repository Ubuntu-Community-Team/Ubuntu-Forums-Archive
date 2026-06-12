---
title: "DisplayPort Audio with Pulse on Thinkpad T510?"
date: 2011-06-16
forum: Hardware
---

### Post by zmjjmz on 2011-06-16
I have a Thinkpad T510 with the NVS 3100M in use (i.e., no Optimus) and I have a DisplayPort -> HDMI cable connected to my TV with a whole stereo system setup. Whenever I tell PulseAudio (either through pavucontrol or the Sound Pref thingie) to use the HDMI as output, nothing comes out. 

However, pavucontrol shows that while audio should be coming out, my speakers disagree. It's not a problem with the TV or the speaker system since I've been able to get other devices working perfectly through HDMI.


Here is the output from aplay -l:

```


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by HermanTheBear on 2011-06-16
I've had this same issue. I too have a 3100M, but on a Dell E6510. I've had the same issue when on Windows 7, but it's a slightly different problem there. In Windows I don't even get the option to use the device, while with Ubuntu I can select it without getting any sound.

---

