---
title: "Onboard sound not working - only available through display port."
date: 2016-01-26
forum: Hardware
---

### Post by Alex_Clibbon on 2016-01-26
I'm not able to hear audio through the front headphone jack, only through my monitor connected to the graphics card. The audio quality through the DP is very low, and I'd rather get the decent quality audio. 

The onboard audio has been enabled in the BIOS, and device is being picked up by ALSA, but does not appear in the list of playback devices or in the sound options menu. 

Is there an obvious step I'm missing to re-enable it?


 [ATTACH=CONFIG]266958[/ATTACH]
[ATTACH=CONFIG]266959[/ATTACH]
[ATTACH=CONFIG]266960[/ATTACH]

---

### Post by matt_symes on 2016-01-28
Hi

> **Alex_Clibbon said:**
> I'm not able to hear audio through the front headphone jack, only through my monitor connected to the graphics card. The audio quality through the DP is very low, and I'd rather get the decent quality audio. 

The onboard audio has been enabled in the BIOS, and device is being picked up by ALSA, but does not appear in the list of playback devices or in the sound options menu. 

It looks like the Intel card is the onboard sound card and the nvidia is the sound card that has the HDMI/DP that you are connecting your monitor to.

> Is there an obvious step I'm missing to re-enable it?

That is the million dollar question. I'll spend some time researching why ALSA may not be seeing the Intel card, later for you. No guarantees I'll have an answer though.

> 
 [ATTACH=CONFIG]266958[/ATTACH]
[ATTACH=CONFIG]266959[/ATTACH]
[ATTACH=CONFIG]266960[/ATTACH]

Please don't post attached images for terminal output. They're more difficult to read and make looking back through a thread harder.

Copy and paste any command posted for you to run, into the terminal. Copy and paste the output from the terminal into the following post between code tags like this

[noparse]```
terminal output
```[/noparse] 

to get output like this 

```
terminal output
```.

E.G
```

matthew-xu-16-04:/home/matthew:3 % lspci -nnk | grep -iA2 audio
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
        Subsystem: TWINHEAD INTERNATIONAL Corp Device [14ff:a00a]
        Kernel driver in use: snd_hda_intel
matthew-xu-16-04:/home/matthew:3 % 
```

So please post the output of this command into your next post, so we can check to see if any driver is being loaded and get the vendor and device IDs.

```
lspci -nnk | grep -iA2 audio
```

Kind regards

---

### Post by Yellow Pasque on 2016-01-28
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

