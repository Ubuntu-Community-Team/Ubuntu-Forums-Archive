---
title: "Upgraded from Bionic to Focal 20.04. My Toshiba Laptop has no sound"
date: 2020-04-27
forum: Hardware
---

### Post by richthommy on 2020-04-27
Just upgraded from Bionic to Focal 20.04. My Toshiba Laptop has no sound. I've done my research to get my sound back. Nothing works.
[https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html](https://www.linuxuprising.com/2018/06/fix-no-sound-dummy-output-issue-in.html)

This is the Output from 18.04
```
lsmod | grep snd_hda_intel
snd_hda_intel          49152  3
snd_hda_codec         135168  3 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel
snd_hda_core           86016  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec
snd_pcm               102400  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd                    86016  16 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi


lspci -nnk | grep -A2 Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Toshiba America Info Systems 5 Series/3400 Series Chipset High Definition Audio [1179:ff1e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
```

This is the Output from 20.04
```
lspci -nnk | grep -A2 Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
        Subsystem: Toshiba Corporation 5 Series/3400 Series Chipset High Definition Audio [1179:ff1e]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel

lsmod | grep snd_hda_intel
snd_hda_intel          53248  3
snd_intel_dspcfg       24576  1 snd_hda_intel
snd_hda_codec         131072  3 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel
snd_hda_core           90112  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec
snd_pcm               106496  4 snd_hda_intel,snd_hda_codec,snd_hda_core
snd                    90112  15 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi

pacmd list-cards
0 card(s) available.
```

---

### Post by slickymaster on 2020-04-27
Moved to a thread of its own and thread tittle edited.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by richthommy on 2020-04-28
Sorry about that. I looked at the Title, as it relates to my issue. The other strange problem is that this is a very old problem. The oldest I've come across seeing is ubuntu 16.04.

---

### Post by richthommy on 2020-04-30
If anybody can help this is the output from alsa-info.sh script  [http://alsa-project.org/db/?f=467624bb63ab4245867c98bab0e8c2ea6be12d0e](http://alsa-project.org/db/?f=467624bb63ab4245867c98bab0e8c2ea6be12d0e)

Looking just about everywhere on the Net, it looks like I might have to re-install Kubuntu.

Now I've done a test with loading UbuntuDDE 20.04 onto a flash drive to see what would happen with the sound. The Sound is working. Below is the output results

Linux ubuntudde 5.4.0-21-generic #25-Ubuntu SMP Sat Mar 28 13:10:28 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


```
lsmod | grep snd_hda_intel
snd_hda_intel          49152  4
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         126976  3 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel
snd_hda_core           90112  4 snd_hda_codec_generic,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec
snd_pcm               106496  3 snd_hda_intel,snd_hda_codec,snd_hda_core
snd                    90112  18 snd_hda_codec_generic,snd_seq,snd_hda_codec_conexant,snd_seq_device,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
```


```
lspci -nnk | grep -A2 Audio
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
    Subsystem: Toshiba Corporation 5 Series/3400 Series Chipset High Definition Audio [1179:ff1e]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

Card: HDA Intel MID                                    F1:  Help               &#9474;
&#9474; Chip: Conexant CX20585                                 F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All               F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: 0.00]
```

[ATTACH=CONFIG]285709[/ATTACH]

---

### Post by tojonukokhadush on 2020-04-30
exactly same problem. but works on earphones. still curious how this can be solved. it says dummy output whenever i change speaker volume in my laptop. tried most of the suggestions in the internet with no luck.

---

