---
title: "Sound Blaster Recon3D / Z-series card shows signal but has no sound output"
date: 2018-04-15
forum: Hardware
---

### Post by backinthesaddle on 2018-04-15
I installed Ubuntu 17.10 yesterday and have most of it running except for my sound card. The sound card itself appears to be recognized and receiving signal, but I can't get any sound to my headphones. Both the card and headphones work on a Windows install. 

```
  
lspci -v | grep Audio

00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
        Subsystem: Gigabyte Technology Co., Ltd Sunrise Point-H HD Audio
        Flags: bus master, fast devsel, latency 32, IRQ 127
        Memory at da140000 (64-bit, non-prefetchable) [size=16K]
        Memory at da120000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [50] Power Management version 3
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Kernel driver in use: snd_hda_intel

02:00.1 Audio device: NVIDIA Corporation GP104 High Definition Audio Controller (rev a1)
        Subsystem: eVga.com. Corp. GP104 High Definition Audio Controller
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at dc080000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [60] Power Management version 3
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Capabilities: [78] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel



06:00.0 Audio device: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series] (rev 01)
        Subsystem: Creative Labs SB1570 SB Audigy Fx
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at dc704000 (64-bit, non-prefetchable) [size=16K]
        Memory at dc700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
        Capabilities: [70] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel
        Capabilities: [170] Device Serial Number 00-00-00-00-00-00-00-00
        Capabilities: [180] Power Budgeting <?>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel








```

Using pavucontrol, in the Configuration tab, I've turned off the GP104 High Definition Audio Controller and the Built-in Audio which just leaves the Sound Core3D [ Sound Blaster Recon 3D / Z-Series](SB1570 SB Audigy FX) set with a profile of Digital Stereo (IEC958) Output.

In the Output Devices tab, the Sound Core 3D is set to a port of Digital Output (S/PDIF). There aren't any other options in the dropdown menu. If I leave YouTube running in the background, I can see the sound signal bobbing up and down so at least I know the sound card is receiving signal. But I can't figure out how to close the remaining gap.

Any ideas?

---

### Post by Yellow Pasque on 2018-04-15
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by backinthesaddle on 2018-04-21
My Alsa info:

[http://www.alsa-project.org/db/?f=48a8e96582dd37b7fe260dc5c559d4a819f9fb96](http://www.alsa-project.org/db/?f=48a8e96582dd37b7fe260dc5c559d4a819f9fb96)

---

### Post by Yellow Pasque on 2018-04-21
Enable these controls in alsamixer (and then maybe restart pulseaudo for good measure:
```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
```

```
alsamixer
pulseaudio -k
```

---

### Post by backinthesaddle on 2018-04-28
I have these settings already, but still no sound through my headphones.

Output from amixer -c 0

```
Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```
I suppose that I could try installing Fedora and see if it recognizes the sound card and then see where the settings differ.

---

### Post by Yellow Pasque on 2018-04-29
They still look disabled to me. Use 'm' key in alsamixer to enable them.

---

### Post by backinthesaddle on 2018-06-23
Ah, sorry. Didn't see this reply. I did go back to alsamixer and change them properly, but there still wasn't any sound. After a lot of googling, it didn't look like the Recon 3D / Z-series was supported, and  Sound Blaster support in general was pretty spotty with Linux for newer cards. It turns out that the easiest solution was just to buy an external USB DAC headphone amp instead and make sure that mine (I bought a FiiO E10K Olympus 2) was Linux-compatible. Works pretty well for me. Thanks for your help though.

---

