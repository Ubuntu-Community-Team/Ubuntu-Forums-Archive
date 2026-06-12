---
title: "Internal Microphone Disabled Upon Plugging In Headphones"
date: 2014-02-02
forum: Hardware
---

### Post by Alex_Gerstenberger on 2014-02-02
The internal microphone in my laptop gets disabled (I assume by the kernel) whenever I plug in a headset or even just headphones. It no longer is listed in my sound options at all. I would expect this behavior for a headset, but not for headphones. The laptop has a single multi-purpose audio jack designed to support headphones or a headset. It does not have a separate microphone jack. Additionally, the microphone on the headset does not work either when it is plugged in, which may be related. I do not particularly care which of the two microphones I use, I simply want either one to work while I have something plugged into the jack, but I figured that getting the internal microphone working would be simpler. Does anyone know of a way to edit my sound settings so that I can achieve this? I have tried [this guide]("https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting"), but it did not solve my issues. I am running Ubuntu 13.10 on an ASUS N550JV.

---

### Post by tgalati4 on 2014-02-02
Open a terminal and post the output of:

```
aplay -l
```

Typically you would add a module switch or an ALSA or pulseaudio configuration switch to fix that behavior.  If this machine is dual boot, does it work consistently in Windows?  

It's possible you have microphone boost turned on and the hardware goes into protect mode when you short the microphone terminal with a stereo headphone (3-ring instead of 4-ring jack).

---

### Post by Yellow Pasque on 2014-02-02
Better yet, just give alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Alex_Gerstenberger on 2014-02-03
Here is the output of aplay:

```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The machine is not dual-booted, but I previously had Windows, and both microphones functioned as expected.

Requested ALSA info is [here]("http://pastebin.com/fC8Rbc55").

Edit: Also checked mic boost in alsamixer, and it was turned all the way up. However, turning it off did not help. Is there another place I should be looking to adjust this?

---

### Post by Yellow Pasque on 2014-02-03
The first thing that jumps out at me is the script failed to recognize ALSA libs:
```
Driver version:     k3.11.0-12-generic
Library version:    
Utilities version:  1.0.27.1
```

1. Try reinstalling libasound2 package (sudo apt-get install --reinstall libasound2). I don't expect that to solve your issue, but it won't hurt..
2. Toggle some of the switches in alsamixer (like automute)
3. Install alsa-tools-gui package and play with 'hdajackretask' program. Perhaps you can override the multi-function jack into being a headphone jack

If none of the above work, file a bug, because most likely, something needs to be resolved at code level (maybe something to do with the phantom mic jack).

---

### Post by Alex_Gerstenberger on 2014-02-03
> **Temüjin said:**
> The first thing that jumps out at me is the script failed to recognize ALSA libs:
```
Driver version:     k3.11.0-12-generic
Library version:    
Utilities version:  1.0.27.1
```

1. Try reinstalling libasound2 package (sudo apt-get install --reinstall libasound2). I don't expect that to solve your issue, but it won't hurt..
2. Toggle some of the switches in alsamixer (like automute)
3. Install alsa-tools-gui package and play with 'hdajackretask' program. Perhaps you can override the multi-function jack into being a headphone jack

If none of the above work, file a bug, because most likely, something needs to be resolved at code level (maybe something to do with the phantom mic jack).

You sir, are a gentleman and a scholar. I reinstalled libasound2, which didn't appear to do anything, but maybe it was one of the issues. However, a combination of overriding the microphone part of the jack in hdajackretask and fiddling with some levels in alsamixer has yielded success; I can now use my laptop's internal microphone while something is plugged into the jack. Thanks a bunch for your help. Cheers.

---

