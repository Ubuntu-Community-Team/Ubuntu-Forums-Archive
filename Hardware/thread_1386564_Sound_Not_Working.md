---
title: "Sound Not Working"
date: 2010-01-20
forum: Hardware
---

### Post by nothankyou on 2010-01-20
Hey folks.  I'm new here, somewhat new to linux in general, and I'm having a little bit of trouble.  I've got no sound!

So! Here's what's going on:

Specs:
ASUS K70i w/Intel Core2 Duo
*Minimal install* Ubuntu 9.10 w/OpenBox
Audio device: nVidia Corporation MCP79 High Definition Audio

I've installed:
alsa
alsa-base
alsa-oss
alsa-tools
alsa-utils
alsactl

Using alsa mixer, I've made sure everything is unmuted.

If it's helpful, lsmod returns the following:

```
sudo lsmod
Module                  Size  Used by
snd_hda_codec_nvhdmi     6048  1 
snd_hda_codec_realtek   277860  1 
snd_hda_intel          31880  1 
snd_hda_codec          87584  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
```If there's anything else I can contribute, please ask, and thanks in advance.

---

