---
title: "Utterly defeated. Can't get sound card to work."
date: 2013-07-11
forum: Hardware
---

### Post by 20goto10 on 2013-07-11
plus I am very new to Linux. I was able to type the following: aplay -l

This is what I got:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I hope someone could explain hot to get this to work, especially as I am new to Linux.

Thanks,

---

### Post by BreezyBrooke on 2013-07-11
After looking up the VT1780S online for Linux compatibility, turns out it has NO support.... You will have to buy a sound card for you PC to get Audio. The sound chip you have is made by VIA which is notorius for horrible Linux support. Most of their hardware, sound, video, ect... will not function under Linux. Sorry.

A good, cheap soundcard that is compatibe would be a Creative Labs SB0570L4 Audigy Card. Get it on Amazon for $25.

---

### Post by 20goto10 on 2013-07-12
Thanks for your help. I really appreciate it.

---

### Post by Yellow Pasque on 2013-07-12
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by 20goto10 on 2013-07-13
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Thank you for your help: [http://www.alsa-project.org/db/?f=03527314f53a64cfdad85b1aa1710d69149f3a0a](http://www.alsa-project.org/db/?f=03527314f53a64cfdad85b1aa1710d69149f3a0a)

---

### Post by Yellow Pasque on 2013-07-13
It looks like you're trying to run JACK and you've removed pulseaudio? Have you set the programs to output to JACK or ALSA instead of pulseaudio?
Try the latest driver: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by 20goto10 on 2013-07-13
It wasn't working from a fresh install. Out of desperation I just started typing in apt-get this and apt-get that. All I am trying to do is get output out of the speakers. I don't want anything than the bare minimum.

---

