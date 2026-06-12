---
title: "ubuntu minimal install"
date: 2009-01-22
forum: Hardware
---

### Post by rizzo0917 on 2009-01-22
Hi, I installed ubuntu minimal install on the first generations eee pc, then with fluxbox as the window manager. Works great, only problem i'm having is no sound. I installed alsa-base , and alsa-oss, and made sure the sound wasn't muted in alsamixer. everything seems to be fine. here is my output for vlc, the only program that gives me a clue

ALSA lib confmisc.c:768:(parse_card) cannot find card '1'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[00000519] oss audio output error: cannot open audio device (/dev/dsp)
[00000519] main audio output error: couldn't find a filter for the conversion
[00000519] main audio output error: couldn't create audio output pipeline

this is /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.17 emulation code)
Kernel: Linux ubuntu 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
HDA Intel at 0xf7eb8000 irq 16

Audio devices:
0: ALC662 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC662 rev1


any help would be great

---

