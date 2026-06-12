---
title: "Software mixing two OSS using apps sound into one stream (ET &amp; Teamspeak) ??"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by brkl on 2006-01-19
I need to play ET and use Teamspeak at the same time. They both use OSS. 

I have a built-in soundchip (Nforce4 AC97) and don't have enough devices to use some of the solutions I've found. They need one full-duplex device and one output only device, but my card has a full-duplex and an INPUT only device, plus a separate output device for digital sound, which I can't use. 

I'm hoping to somehow use a wrapper to send the streams from TS and ET to ESD or some other sound server, which would mix the sound into one stream and send to /dev/dsp. 

```
usr@ubuntu:~$ ls -l /dev/*dsp*
crw-rw----  1 root audio 14, 12 2006-01-19 18:44 /dev/adsp
crw-rw----  1 root audio 14,  3 2006-01-19 18:44 /dev/dsp

```

```
usr@ubuntu:~$ cat /proc/asound/cards
0 [CK804          ]: NFORCE - NVidia CK804
                     NVidia CK804 with ALC850 at 0xf0100000, irq 22

```

```
usr@ubuntu:~$ cat /proc/asound/pcm
00-00: Intel ICH : NVidia CK804 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : NVidia CK804 - MIC ADC : capture 1
00-02: Intel ICH - IEC958 : NVidia CK804 - IEC958 : playback 1

```

---

