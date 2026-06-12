---
title: "No sound at all"
date: 2006-10-20
forum: Hardware &amp; Laptops
---

### Post by infinite84 on 2006-10-20
Could need some help with my "no sound" problem.
I am running Ubuntu Dapper 6.06 LTS on my laptop, which is a Asus F3JA.

Problem characteristics:
No sound at all! But I can play mp3s in XMMS without it yelling at me, so it plays but i dont hear anything. And no the volume is not muted :P
I've followed numerous guides but i haven't been able to solve this problem.
What i can tell from the output below, ubuntu detects my soundcard...but whats the problem...
Some help would bee appreciated.

relevant output from: lspci -v

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1338
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>


output from: lsmod | grep -i snd

snd_hda_intel          18964  1
snd_hda_codec         157616  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

---

### Post by Kateikyoushi on 2006-10-20
Did you try to mute external amplifier in alsamixer ? As long as it was  on I had no sound at all, and as long my headphone jack sese was on only the headphone jack worked the internal speakers did not.

---

### Post by infinite84 on 2006-10-21
yes, i have tried that to. Dont get any sound in my headphones either.

---

### Post by mikaPELL on 2006-11-20
Same problem, same computer. Bump?

---

### Post by simpor on 2007-02-25
Same computer same problem... some info: 


lspci | grep -i audio
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

cat /proc/asound/modules
```

 0 snd_hda_intel

```

cat /proc/asound/cards
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 169

```

lsmod | grep snd
```

snd_hda_intel          20116  1
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

amixer
```

Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Front',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 89 [387%] [on]
  Front Right: Playback 89 [387%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 23 [100%] [on]
  Front Right: Playback 23 [100%] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 13 [100%] [off]
  Front Right: Capture 13 [100%] [off]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'CD'
  Item0: 'Mic'

```

aplay -l
```

**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: ALC861 Analog [ALC861 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0
kort 0: Intel [HDA Intel], enhet 1: ALC861 Digital [ALC861 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet #0: subdevice #0

```

ls -al /dev/snd/*
```

crw-rw---- 1 root audio 116, 6 2007-02-24 20:54 /dev/snd/controlC0
crw-rw---- 1 root audio 116, 5 2007-02-24 20:54 /dev/snd/pcmC0D0c
crw-rw---- 1 root audio 116, 4 2007-02-24 20:54 /dev/snd/pcmC0D0p
crw-rw---- 1 root audio 116, 3 2007-02-24 20:54 /dev/snd/pcmC0D1p
crw-rw---- 1 root audio 116, 2 2007-02-24 20:53 /dev/snd/timer

```

---

