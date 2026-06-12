---
title: "No Sound on via 8237"
date: 2006-04-11
forum: Hardware &amp; Laptops
---

### Post by phyre-x on 2006-04-11
hey, just got ubuntu installed on my laptop, got ralink wireless going nicely and thought it was worth a try to see if anyone can help me figure out my sound. i know the sound hardware works because it did under windows. i tried the solution on the ubuntuguide to no avail. im very new to linux and tbh dont understand much but would like to. heres the output from lsmod grep snd

phyre@ubuntu:~$ lsmod | grep snd
snd_via82xx_modem      15492  0
snd_seq_dummy           3620  0
snd_seq_oss            33600  0
snd_seq_midi            9088  0
snd_seq_midi_event      6848  2 snd_seq_oss,snd_seq_midi
snd_seq                50736  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            28576  0
gameport               14824  1 snd_via82xx
snd_ac97_codec         83932  2 snd_via82xx_modem,snd_via82xx
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  4 snd_via82xx_modem,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  2 snd_seq,snd_pcm
snd_page_alloc         10600  3 snd_via82xx_modem,snd_via82xx,snd_pcm
snd_mpu401_uart         7296  1 snd_via82xx
snd_rawmidi            24704  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8460  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    54884  12 snd_via82xx_modem,snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9600  1 snd

i noticed that there is an intergrated modem that has been installed and is acting as an audio device apparently so maybe somehow disabling that would help ? if i knew how anyway :confused:

---

