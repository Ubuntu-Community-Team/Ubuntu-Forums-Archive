---
title: "[SOLVED] Alsa issue on iMac"
date: 2008-11-10
forum: General Help
---

### Post by AlainJLEB on 2008-11-10
Hi there,

After the upgrade from 8.04 to 8.10, there is no sound anymore, despite the fact that Alsa detects a card:
```
lshw -C multimedia
  *-multimedia
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
root@imac:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@imac:~# ls /proc/asound/
card0  cards  devices  hwdep  Intel  modules  oss  pcm  seq  timers  version

```
However, when looking at above outputs, one is mentioning ALC8889 and another ALC885 ... I have already compiled again and installed Alsa from source, but it does not help.

Any idea on what could be the root cause? Should I compile Alsa in full-debug mode to get more info?

---

### Post by AlainJLEB on 2008-11-12
Solved following this [link]("http://https://help.ubuntu.com/community/HdaIntelSoundHowto").

---

