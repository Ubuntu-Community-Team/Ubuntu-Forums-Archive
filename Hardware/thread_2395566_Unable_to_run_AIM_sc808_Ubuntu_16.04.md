---
title: "Unable to run AIM sc808 Ubuntu 16.04"
date: 2018-07-03
forum: Hardware
---

### Post by el-manfref on 2018-07-03
I was trying to run my sound card, unfortunately without success.
Link to my alsainfo: [http://www.alsa-project.org/db/?f=b7181d4360ecca1fd1279da0439d97193fffd113](http://www.alsa-project.org/db/?f=b7181d4360ecca1fd1279da0439d97193fffd113)

---

### Post by #&amp;thj^% on 2018-07-03
Humm?
is there any sound  output when running this in the terminal:
```
speaker-test -t wav -c 6
```

---

### Post by el-manfref on 2018-07-04
speaker-test 1.1.0

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 6,951706
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 4,967260
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 4,949964
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 4,963193
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 4,938645
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE

---

### Post by el-manfref on 2018-07-04
Does "Kernel driver in use" for  05:00.0 Audio device: C-Media Electronics Inc CM8888 [Oxygen Express] is wrong? Cuz if i'm correct CM8888 it should use  snd_hda_codec_cmedia

lspci -v | grep -A7 -i "audio" 

 00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
    Subsystem: ASRock Incorporation 8 Series/C220 Series Chipset High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f3230000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
--
01:00.1 Audio device: NVIDIA Corporation Device 10f0 (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device 3701
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f3080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

--
05:00.0 Audio device: C-Media Electronics Inc CM8888 [Oxygen Express]
    Subsystem: C-Media Electronics Inc HDA Controller
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at f3100000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

---

### Post by #&amp;thj^% on 2018-07-04
What I wanted to know>> was there any sound from running the speaker test? :)

---

### Post by el-manfref on 2018-07-04
Not from soundcard. Only from built in

---

