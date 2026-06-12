---
title: "Pipewire crash my USB audio stream"
date: 2022-07-02
forum: Hardware
---

### Post by hitodev on 2022-07-02
With Ubuntu 22 and PopOS 22 (Ubuntu-based) Pipewire crash my  USB/DAC audio output to my Northern Star Design USB dac32 DAC.


[LIST]
[*]I'm sure this is not a problem related to the USB cable quality (computer is connected to DAC with an audiophile grade Supra USB cable).
[*]The problem occurs with all USB ports
[*]it is not related to the audio app I use (Lollypop, VLC)
[*]It occurs only when "Analog Output - USB Hi-Speed Interface" output device is selected
[/LIST]

Problem :

Near every time (3/4) I get and extremely loud white noise on playback.
When I reduce  the volume (close to 0) sound appears.
It seems to me the output level is too high, causing saturation.

I tried to create a "gate" filter (-32db) with EasyEffect but when I launch an another app (VLC, youtube) in parallel to my current audio player (Lollypop), the audio crash again.

Finally I have reinstalled a PopOS 21 version (pulseaudio).

With Pulseaudio the North Star Design DAC works perfectly,
even with a tuned config file for up-sampling to 192KHz with this recommendations: [https://medium.com/@gamunu/enable-high-quality-audio-on-linux-6f16f3fe7e1f](https://medium.com/@gamunu/enable-high-quality-audio-on-linux-6f16f3fe7e1f)).

Hardware:
mobo: GA-Z77X-UD3H-WB WIFI
Intel® Core&#8482; i7-3770S CPU @ 3.10GHz × 8
NV98 / Intel® HD Graphics 4000 (IVB GT2)

DAC
North star design USB dac32

---

### Post by #&amp;thj^% on 2022-07-06
Late Reply Sorry.
I was worried that Canonical would treat Pipewire/Wireplumber as a Redheaded step child.
I wish I had your Dac device, I would love to play with it on a different Linux OS.
I really enjoy all the benefits that Pipewire/Wireplumber has brought to my system.
```
wpctl status
PipeWire 'pipewire-0' [0.3.53, me@arch-me, cookie:<Snip>]
 &#9492;&#9472; Clients:
        31. WirePlumber                         [0.3.53, me@arch-me, pid:1085]
        32. xfce4-pulseaudio-plugin             [0.3.53, me@arch-me, pid:1056]
        33. pipewire-pulse                      [0.3.53, me@arch-me, pid:1089]
        35. WirePlumber [export]                [0.3.53, me@arch-me, pid:1085]
        54. xdg-desktop-portal                  [0.3.53, me@arch-me, pid:6209]
        61. Strawberry device finder            [0.3.53, me@arch-me, pid:75425]
        62. strawberry                          [0.3.53, me@arch-me, pid:75425]
        68. wpctl                               [0.3.53, me@arch-me, pid:79405]

Audio
 &#9500;&#9472; Devices:
 &#9474;      43. HDA NVidia                          [alsa]
 &#9474;      44. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      55. SRS-XB22                            [bluez5]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      51. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.29]
 &#9474;  *   56. SRS-XB22                            [vol: 0.39]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   52. Family 17h/19h HD Audio Controller Analog Stereo [vol: 0.74]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        63. strawberry                                                  
             65. output_FL       > SRS-XB22:playback_FL
             67. output_FR       > SRS-XB22:playback_FR

Video
 &#9500;&#9472; Devices:
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;      42. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   45. Integrated Camera                  
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    bluez_output.F8_DF_15_7F_64_73.a2dp-sink
         1. Audio/Source  alsa_input.pci-0000_05_00.6.analog-stereo


```
My humble little system:
```
inxi -MCA
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> UEFI: LENOVO v: EUCN37WW date: 04/14/2022
CPU:
  Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1473 min/max: 1400/3000 cores: 1: 1919 2: 1399 3: 1397
    4: 1396 5: 1397 6: 1445 7: 1746 8: 1392 9: 1397 10: 1397 11: 1397 12: 1397
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.18.9-zen1-1-zen running: yes
  Sound Server-2: PipeWire v: 0.3.53 running: yes


```

Perhaps have another Go at it, with a look at this:[https://wiki.archlinux.org/title/PipeWire#Audio_is_distorted](https://wiki.archlinux.org/title/PipeWire#Audio_is_distorted)

---

