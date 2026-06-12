---
title: "Sound Card is Detected But Doesn't Work"
date: 2010-08-15
forum: Hardware
---

### Post by alex.nucleo on 2010-08-15
Hi dear community.
I'm trying to setup my sound card to work in the latest Ubuntu 10.04 Lucid Lynx. The sound card is successfully detected as you can see in the listing below:
> 
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: DX [Xonar DX], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: DX [Xonar DX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
You can also see that I have actually 2 sound controllers: built in audio codecs and Asus Xonar DX.
Built in codecs work ok, but I cannot make Asus card working.
When I open Sound Preferences, I see only built in codecs in the list (see attached screenshot).
When I run alsamixer, I see all channels unmuted for the sound card (screenshot attached).
VLC plays nothing, even when I manually select Asus Xonar card in the settings.
> aplay /usr/share/sounds/alsa/Front_Center.wav plays nothing either, but output says it's trying to play:
> Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, MonoI have ALSA 1.0.22 currently installed and kernel 2.6.32-24.
Sound card itself should be OK, because Windows can play sound on it.

Please, advise any additional steps I can take to make it working.

Thanks!

---

### Post by alex.nucleo on 2010-08-16
Nobody can help?

---

### Post by uberlube on 2010-08-18
disable onboard sound in your bios

---

### Post by alex.nucleo on 2010-08-20
> **uberlube said:**
> disable onboard sound in your bios

Thanks a lot, this works like a charm!

---

