---
title: "Disable onboard sound - blacklist doesn't work"
date: 2008-11-09
forum: Hardware
---

### Post by mattyb515 on 2008-11-09
Let me start off by saying I'm running UbuntuStudio 64.  I've got an onboard soundcard as well as a M-Audiophile 192.  I think I'm running into some conflicts and would like to disable the onboard sound which is AC97.  I've already gone through the BIOS to try that way but it still comes up.  I've also looked through previous posts and gone the route of blacklisted the modules but that didn't work and there are a bunch of sound modules listed.  If someone can give some help on how to do this I'd really appreciate it.

Below is what's listed for sound when I do lsmod:
snd_rtctimer            5344  1 
snd_ice1724           110468  2 
snd_ice17xx_ak4xxx      5888  1 snd_ice1724
snd_ak4114             12800  1 snd_ice1724
snd_pt2258              6400  1 snd_ice1724
snd_i2c                 7936  2 snd_ice1724,snd_pt2258
snd_ak4xxx_adda        10880  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_seq_dummy           5764  0 
snd_via82xx            33960  2 
gameport               18704  1 snd_via82xx
snd_via82xx_modem      18956  0 
snd_seq_oss            39424  0 
snd_ac97_codec        123992  3 snd_ice1724,snd_via82xx,snd_via82xx_modem
snd_mpu401_uart        11392  2 snd_ice1724,snd_via82xx
ac97_bus                4224  1 snd_ac97_codec
snd_pcm_oss            48032  0 
snd_seq_midi           10688  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_seq_midi_event     10240  2 snd_seq_oss,snd_seq_midi
snd_seq                64256  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                93320  6 snd_ice1724,snd_ak4114,snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            30240  2 snd_mpu401_uart,snd_seq_midi
snd_timer              28424  3 snd_rtctimer,snd_seq,snd_pcm
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_page_alloc         13200  3 snd_via82xx,snd_via82xx_modem,snd_pcm
snd                    71880  28 snd_rtctimer,snd_ice1724,snd_ak4114,snd_pt2258,snd_i2c,snd_ak4xxx_adda,snd_seq_dummy,snd_via82xx,snd_via82xx_modem,snd_seq_oss,snd_ac97_codec,snd_mpu401_uart,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_rawmidi,snd_timer,snd_seq_device
soundcore              11040  1 snd

Again, any and all help is greatly appreciated.  I'm hoping this helps to solve some of my sound issues.

---

