---
title: "Asus Xonar Phoebus Solo - CM8888"
date: 2016-08-06
forum: Hardware
---

### Post by marcodasilva26 on 2016-08-06
Hello,

I'm running Ubuntu 16.04, i have an Asus Xonar Phoebus Solo  sound card, and while it is recognized it outputs no sound whatsoever.  Any ideas on  how to put this to work? 

Thanks

```
$ LC_ALL=C aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: CMedia [HDA C-Media], device 0: CMI8888 Analog [CMI8888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMedia [HDA C-Media], device 1: CMI8888 Digital [CMI8888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by Yellow Pasque on 2016-08-07
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by marcodasilva26 on 2016-08-07
Here you go.... 

[http://www.alsa-project.org/db/?f=09078ceb057bbe41175aca3d3d5cec25d96c9d33](http://www.alsa-project.org/db/?f=09078ceb057bbe41175aca3d3d5cec25d96c9d33)

---

### Post by Yellow Pasque on 2016-08-07
It certainly looks like you have the volume controls unmuted and turned up. I don't see anything obviously wrong from your information. (As always, I don't claim to be an expert.) I am a bit curious why there's nothing in the dmesg section of the log.

- You do have the Phoebus device selected (i.e. not the HDMI) in the volume control, correct?
- Have you tried headphones?

There haven't been a lot of changes to the kernel module for CMI888, but if you would like to try the latest kernel driver/module code, see: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

