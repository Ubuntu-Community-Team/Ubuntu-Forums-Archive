---
title: "No sound output at all."
date: 2011-12-23
forum: Hardware
---

### Post by abtekk on 2011-12-23
Toshiba NB200-12U
Xubuntu 10.04 (LTS)
32-bit
Up to date system

I've just installed xubuntu on my friends netbook (model above). And I have no sound output, I have checked the obvious options in the mixer and on none of the options is anything muted. I have the options in the mixer list:

HDA Intel (ALSA mixer)
Realtek ALC272 (OSS mixer)
Playback: Internal audio analog stereo (Pulsaudio mixer)
Capture: Monitor of internal audio analog stereo (Pulseaudio mixer)
Capture: Internal audio analog stereo (Pulseaudio mixer)

--------------------

aplay -l gives the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
keegan@keegan-laptop:~$ 

```

---

### Post by Bucky Ball on 2011-12-23
Change this:

Realtek ALC272 (OSS mixer)

... to this:

Realtek ALC272 (ALSA mixer)

Also, do you have gnome ALSA mixer installed?

---

### Post by abtekk on 2011-12-23
SOLVED.

Found info on another thread that suggested adding this

options snd-hda-intel model=auto

To alsa-conf and it worked. Thanks anyway.

---

### Post by Bucky Ball on 2011-12-23
Good news. Enjoy!

---

