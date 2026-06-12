---
title: "Audio asus F3JA mistake"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by el-loco on 2007-04-02
I have an asus F3JA laptop with Ubuntu edgy eft:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

and with the latest ALSA driver.
The problem is that the audio is playing only if i insert a jack into the laptop, and it's playing from the laptop speakers and not from the dolby or hadphones, when I remove the jack from the laptop it stop playing.
And in the alsamixer the Front controller is always disabled.

Some Info:

0 snd_hda_intel

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 58

snd_hda_intel          21528  1
snd_hda_codec         172544  1 snd_hda_intel
snd_pcm_oss            47232  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84996  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           5124  0
snd_seq_oss            38144  0
snd_seq_midi            9984  0
snd_rawmidi            27136  1 snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                59760  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9868  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    60676  13 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm

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
  Front Left: Playback 48 [19%] [-41.40dB]
  Front Right: Playback 48 [19%] [-41.40dB]
Simple mixer control 'Front',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 17 [74%] [15.00dB] [off]
  Front Right: Playback 17 [74%] [15.00dB] [off]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 17 [74%] [15.00dB] [on]
  Front Right: Playback 17 [74%] [15.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 17 [74%] [15.00dB] [off]
  Front Right: Playback 17 [74%] [15.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 0 [0%] [-6.00dB] [on]
  Front Right: Capture 0 [0%] [-6.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'CD'
  Item0: 'Mic'

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: ALC861 Analog [ALC861 Analog]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: ALC861 Digital [ALC861 Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

totale 0
drwxr-xr-x  2 root root     160 2007-04-03 00:06 .
drwxr-xr-x 13 root root   13760 2007-04-03 00:38 ..
crw-rw----  1 root audio 116, 7 2007-04-03 00:06 controlC0
crw-rw----  1 root audio 116, 6 2007-04-03 00:06 pcmC0D0c
crw-rw----  1 root audio 116, 5 2007-04-03 00:06 pcmC0D0p
crw-rw----  1 root audio 116, 4 2007-04-03 00:06 pcmC0D1p
crw-rw----  1 root audio 116, 3 2007-04-03 00:06 seq
crw-rw----  1 root audio 116, 2 2007-04-03 00:06 timer

---

