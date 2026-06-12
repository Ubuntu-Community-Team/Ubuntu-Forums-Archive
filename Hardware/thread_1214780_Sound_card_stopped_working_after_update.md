---
title: "Sound card stopped working after update"
date: 2009-07-16
forum: Hardware
---

### Post by lads on 2009-07-16
I'm running Ubuntu 9.04 on a Vaio FW31 since a few months back; up to now the sound board worked perfectly without any intervention of mine.

Yesterday, after an update, it simply stopped reproducing the sound correctly. All I get is some strange noise whenever I try to play music or when GNOME emits some sound.

I ran a few commands, from which I can see no wrong:

```
lads@MDK:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

lads@MDK:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lads@MDK:~$ sudo lshw -C sound
[sudo] password for lads: 
  *-multimedia            
       description: Audio device
       product: RV635 Audio device [Radeon HD 3600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

Any ideas? Thanks for the help.

---

### Post by lads on 2009-07-16
:confused:

I just found out that the PCM channel was turned off. I have no idea how it happened. Could an update do something like resetting the sound card config?

Thanks and sorry for bothering.

---

