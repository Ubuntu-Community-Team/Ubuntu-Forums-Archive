---
title: "No sound with ubuntu 20.04"
date: 2020-06-25
forum: Hardware
---

### Post by todaug on 2020-06-25
Hello, I got a new chromebook pixel slate and I installed crouton on it which comes up with an installation of an xfce ubuntu 16.04. I decided to upgrade my distribution all the way up to 20.04, but now I cannot manage to make my sound to work.

I have alsa, alsa-utils and pulseaudio installed but pavucontrol does not seems to find my sound cards at all.

If I execute this command 

```
aplay -l
```

the command throw me this

```
aplay: device_list:274: no soundcards found...
```

but if I use sudo

```
sudo aplay -l
```

I can see my devices

```
**** List of PLAYBACK Hardware Devices ****
card 0: kblmax98373 [kblmax98373], device 0: Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: kblmax98373 [kblmax98373], device 4: Hdmi1 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: kblmax98373 [kblmax98373], device 5: Hdmi2 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: kblmax98373 [kblmax98373], device 6: Hdmi3 (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I have tried many things that I found on different forums, but without success.

I'm also not really familiar with alsamixer, so I'm not really sure what I can do with it, but I can see my kblmax98373 if I press F6

---

