---
title: "HP Pavillion dv1000 No Sound"
date: 2010-01-06
forum: Hardware
---

### Post by Nerfair on 2010-01-06
Hi guys! I am new to Ubuntu, just installed it to my dv1000 and have no sound, what i must do to install it? 

part of lspci: ```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
```Ubuntu 9.10 :)

**$ cat /proc/asound/oss/sndstat**
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux localhost 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
--- no soundcards ---

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG
```**$ cat /proc/asound/version**
```
Advanced Linux Sound Architecture Driver Version 1.0.20.
```[B]$ lsmod |grep snd 
[/B]```

snd_intel8x0           30168  0 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm

```

**$ alsamixer**
```

function snd_ctl_open failed for default no such file or directory

```

---

