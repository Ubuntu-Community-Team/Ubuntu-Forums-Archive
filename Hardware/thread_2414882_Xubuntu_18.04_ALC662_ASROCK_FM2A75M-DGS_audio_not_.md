---
title: "Xubuntu 18.04 ALC662 ASROCK FM2A75M-DGS audio not working"
date: 2019-03-16
forum: Hardware
---

### Post by nlona on 2019-03-16
I cannot hear any sound out of My mb asrock fm2a75m-dgs all sound port look unplugged even if music speaker 2 way USB powered https://www.trust.com/it/product/20943-polo-compact-2-0-speaker-set jack 3.5 are connected to the green back port, eventuali smartphone headset or budget chinese headset does not work. Following some video, images and logs. I tried most of snd Intel driver option (such as asrock-mo, generic or auto).
https://forum.ubuntuusers.de/topic/alc662-kein-ton-von-asrock-fm2a75m-dgs/

 The problem was also on 16.04 xubuntu
https://forum.ubuntuusers.de/topic/audio-problem-wie-folgend/[Previous german thread on xubuntu 16.04](https://forum.ubuntuusers.de/topic/audio-problem-wie-folgend/)
```
hp@hp-desktop:~$ lsb_release && uname -a && cat /proc/asound/cards && aplay -l && lspci -nnk |grep -iA2 audio && ps -C esd && ps -C arts && ps -C pulseaudio
No LSB modules are available.
Linux hp-desktop 4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe100000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe080000 irq 19
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Generic [HD-Audio Generic], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 3: HDMI 0 [HDMI 0]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 7: HDMI 1 [HDMI 1]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: NVidia [HDA NVidia], dispositivo 8: HDMI 2 [HDMI 2]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 01)
	Subsystem: ASRock Incorporation FCH Azalia Controller [1849:7662]
	Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device [0403]: NVIDIA Corporation GP107GL High Definition Audio Controller [10de:0fb9] (rev a1)
	Subsystem: eVga.com. Corp. GP107GL High Definition Audio Controller [3842:6251]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
  PID TTY          TIME CMD

```
[Alsamixer](https://imgur.com/a/X1wDkrI)
[VideoPavucontrol]( https://streamable.com/11yr)

---

