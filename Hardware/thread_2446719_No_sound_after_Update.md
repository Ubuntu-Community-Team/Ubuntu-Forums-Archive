---
title: "No sound after Update"
date: 2020-07-05
forum: Hardware
---

### Post by cjgump720 on 2020-07-05
System is a repurposed Dell Vostro 470 running Ubuntu 18.04, connected to an HDTV over an HDMI cable. I've been using it as a HTPC for over a year with no issues. I just installed a system update, and now I have no sound.

Forum posts about sound problems seem common, and I've tried following solutions posted online, with no luck.  Here's some of the info asked for in other posts. I don't know enough to know what's important.

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Output snipet from inxi -Fz

```
Graphics:  Card: NVIDIA GK107 [GeForce GT 740]
           Display Server: x11 (X.Org 1.20.8 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: GeForce GT 740/PCIe/SSE2
           version: 4.6.0 NVIDIA 440.100
Audio:     Card-1 Intel 7 Series/C216 Family High Def. Audio Controller
           driver: snd_hda_intel
           Card-2 NVIDIA GK107 HDMI Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k5.3.0-62-generic

```

pavucontrol lists my Nvidia card, with the output device port as HMDI/DisplayPort 2

alsamixer lists both the Intel and  Nvidia cards.  The Nvidia S/PDIF and S/PDIF 1 are not muted.

The Sound Settings has HDMI/DisplayPort 2 - GK107 HDMI Audio Controller listed, and the sound test on the HDMI/DisplayPort 2 yields no sound.

One thing that jumps out at me is that inxi lists the audio controller driver as snd_hda_intel. Should that be an Nvidia driver? If I look under Software & Updates, Additional Drivers says I'm using the recommended driver for the GK 107 (nividia-driver-440). I've tried reinstalling the drivers just in case, but no change.

I appreciate any help.

Thanks!

chris

---

### Post by cjgump720 on 2020-07-05
I'm an idiot.  The TV was on mute.

---

