---
title: "Ubuntu 21.04 desktop - Popping sound from speakers on Ubuntu start up and shut down."
date: 2021-06-07
forum: Hardware
---

### Post by baetard on 2021-06-07
Hi,


This problem will happen booting into Windows too if the analog audio jacks aren't set properly in the Realtek software.


My audio is onboard Realtek 1220 HB. The motherboard has 3 analog jacks in the back that can be configured in various ways by the Realtek software. Currently, I have front speakers (L&R) connected to one jack, and center (center and sub) connected to another. The popping appears to be coming from the sub/center. This jack, according to the motherboard manual, is to be used for center/sub, but can also be a mic jack. In Windows, I just launch the Realtek software and 'tell it' which things are connected to the audio jacks. No more popping on startup and shut down.


What do?


P.S. I used experience those same pops while running Ubuntu but adding


* options snd-hda-intel power_save=0 power_save_controller=N*

to *alsa-base.conf* stopped that.

What do?

Thanks

---

