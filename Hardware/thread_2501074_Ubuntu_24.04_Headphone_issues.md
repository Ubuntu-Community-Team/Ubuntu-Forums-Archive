---
title: "Ubuntu 24.04: Headphone issues"
date: 2024-09-22
forum: Hardware
---

### Post by crypterr on 2024-09-22
Hi,

First time on ubuntu - please excuse the noob-level questions!

Installed ubuntu 24.04 on a samsung galaxy book 3 360. Strange audio issue though - on plugging in headphones (any headphones), there used to be just a buzzing sound in place of an audio track whenever a music/ video track plays. This if I increased the volume to the max (after enabling Overamplification in Settings) - otherwise there was no sound in the headphones.

Followed instructions available at [https://www.reddit.com/r/linuxhardware/comments/xzxkef/comment/jq0z9ln/](https://www.reddit.com/r/linuxhardware/comments/xzxkef/comment/jq0z9ln/) - this helped slightly reduce the buzzing sound in the headphones, and I can actually hear some audio now. However the volume is very, very low - even at max (overamplified) volume... :(

Basically, what I did was to add the following 3 lines to the end of the alsa-base.conf file at /etc/modprobe.d/
```
options snd-intel-dspcfg dsp_driver=1
options snd-hda-intel model=dell-headset-multi
options snd-hda-intel power_save=1
```

Have tried fiddling with alsamixer, but to no avail.

Would appreciate any help!

Here is the output of inxi -A
```
Audio:
  Device-1: Intel Raptor Lake-P/U/H cAVS driver: snd_hda_intel
  API: ALSA v: k6.8.0-45-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active

```

And here is the output of aplay --list-devices
```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC256 Analog [ALC256 Analog]
  Subdevices: 0/1
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

```

Note: Tried the potential fixes in the following webpages, but no success
[LIST]
[*][https://askubuntu.com/questions/1511648/audio-not-working-ubuntu-24-04](https://askubuntu.com/questions/1511648/audio-not-working-ubuntu-24-04) 
[*][https://forums.linuxmint.com/viewtopic.php?t=374146](https://forums.linuxmint.com/viewtopic.php?t=374146) 
[/LIST]

---

### Post by edfelt on 2024-10-17
I have the same issue. Here is my audio info:


sudo lshw -C sound
  *-multimedia:0 UNCLAIMED  
       description: Multimedia controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm cap_list
       configuration: latency=0
       resources: iomemory:600-5ff memory:603c000000-603cffffff
  *-multimedia:1
       description: Multimedia audio controller
       product: Raptor Lake-P/U/H cAVS
       vendor: Intel Corporation
       physical id: 1f.3
       bus info: pci@0000:00:1f.3
       logical name: card0
       logical name: /dev/snd/controlC0
       logical name: /dev/snd/hwC0D0
       logical name: /dev/snd/hwC0D2
       logical name: /dev/snd/pcmC0D0c
       logical name: /dev/snd/pcmC0D0p
       logical name: /dev/snd/pcmC0D31p
       logical name: /dev/snd/pcmC0D3p
       logical name: /dev/snd/pcmC0D4p
       logical name: /dev/snd/pcmC0D5p
       logical name: /dev/snd/pcmC0D6c
       logical name: /dev/snd/pcmC0D7c
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=sof-audio-pci-intel-tgl latency=64
       resources: iomemory:600-5ff iomemory:600-5ff irq:243 memory:603e1e0000-603e1e3fff memory:603e000000-603e0fffff

---

