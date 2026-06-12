---
title: "Asus ux430uar no sound"
date: 2018-01-13
forum: Hardware
---

### Post by dleshko on 2018-01-13
Please, can somebody help me?
I have laptop Asus ux430uar and no any sound. Try to find in Google, but no any helpful info.
Ubuntu 17.10

**This is output from "inxi -Fxzd"**:
Audio:     Card Intel Device 9d71 driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.13.0-25-generic

**Output from "aplay -l":**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC294 Analog [ALC294 Analog]
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

---

### Post by Yellow Pasque on 2018-01-13
First, try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) 

If sound does not work after reboot, get more information:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by dleshko on 2018-01-14
Install dkms, but still no sound.

This is result of "Alsainfo":
[http://www.alsa-project.org/db/?f=5084f1b6e4713b63568024a49746853c2501d960](http://www.alsa-project.org/db/?f=5084f1b6e4713b63568024a49746853c2501d960)

---

### Post by dleshko on 2018-01-14
Strange things: reboot to Win 10 and also no sound. Go to BIOS, drop all settings to default and, who knows, I have sound! It's a magic?!

---

