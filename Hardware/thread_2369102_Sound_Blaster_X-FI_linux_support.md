---
title: "Sound Blaster X-FI linux support"
date: 2017-08-18
forum: Hardware
---

### Post by hound5777 on 2017-08-18
Hi All

Just wondered if anyone has ever got one of the newer Sound Blaster card's working on Linux? I have trawled the internet but no existing fixes work for the card (Sound Blaster X-FI MB5).

Any help would be much appreciated :)

Thanks

---

### Post by handydandyhim on 2017-08-18
Have you tried here?
[http://manpages.ubuntu.com/manpages/yakkety/man7/oss_sbxfi.7.html](http://manpages.ubuntu.com/manpages/yakkety/man7/oss_sbxfi.7.html)

Also, can you reply with the results of the following in terminal:
```
aplay -l
```

---

### Post by hound5777 on 2017-08-19
Hi

Thanks for the quick reply - I did find that but the download gives 1 file, which when extracted has a .7 extension. What should I do with it?

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1220 Analog [ALC1220 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1220 Digital [ALC1220 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by hound5777 on 2017-08-19
Just gets stranger...

So the link provider (I believe) is now part of OSS4 - but with that installed and alsa + pulseaudio gone - no difference.

Quickly put on Windows 10 to double check it wasn't an issue with the laptop and the sound card showed as Realtek Audio (and worked fine).

Put Ubuntu back on, connected an external monitor and the speakers started working. Doesn't survive a reboot though.

---

