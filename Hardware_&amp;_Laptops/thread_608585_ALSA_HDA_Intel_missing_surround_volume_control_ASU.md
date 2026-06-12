---
title: "ALSA HDA Intel missing surround volume control ASUS Laptop"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by Forvrknight on 2007-11-10
I'm fairly new at Linux Ubuntu being my first go at it.

In 7.04 I had the option to control Front and Surround which turned up all the speakers on my Asus G2P-7R001M laptop. After upgrading to 7.10 I can't find the surround volume only the front. The front volume only controls the small speakers in my laptop and it's driving me batty.

Here is the output from Aplay -l

Audio Controller (rev 02)
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

From lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


Not sure what else to do. I have attempted to upgrade ALSA drivers but that didn't work and I had to reload my install. Does anyone have any suggestions?

---

### Post by Forvrknight on 2007-11-10
Never mind I fixed it after quite a bit of searching.

Added options snd-hda-intel model=6stack-dig to the end of /etc/modprobe.d/alsa-base

So now I get 
Front - teeny speakers
Center - Front left
LFE - Front right

3stack-dig worked too but the one added sounded better and had more volume output.

:guitar:

Now if i can just get my keyboard volume to control all of them since it is now randomly deciding which one to control even though I have them all selected in the volume control.

---

