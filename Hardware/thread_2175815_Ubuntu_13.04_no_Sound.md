---
title: "Ubuntu 13.04 no Sound"
date: 2013-09-21
forum: Hardware
---

### Post by tande2 on 2013-09-21
Hi Folks!
I am beginner here and I nee your help to solve my problem.
I am not a ignorant guy, and before to post my request for help here I already browsed the internet and did't get what I need.

I have a Ubuntu 13.04 and it is without sound, both as speaker in headset.
I am using HDA Intel (Alsa Mixer) control, and speaker or headset are enabled.
I will show to you some informations abou software and configuration.
Please, ask me what you wish to help me to solve my problem.

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

$ lsmod | grep snd
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63791  1 
snd_hda_intel          38307  6 
snd_hda_codec         117617  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  4 snd_hda_codec_si3054,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  21 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd

---

### Post by Yellow Pasque on 2013-09-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by YesKah on 2013-09-24
Some days ago, I  do the latest update, a similar phenomenon occurred.
Try insertion and removal of plugconnecting several time.
It might be solved for the time being.

My &#65328;&#65315;&#65306;emachines J4470
&#65315;&#65328;&#65333;&#65306;Athlon 64x2 2.1GHz
Memory&#65306;&#65300;&#65319;ib
Graphic chip&#65306;nvidia
Ubuntu Version&#65306;Ubuntu Studio 12.04.3 LTS 64bit
Sound chip:Realtec High Difinition

---

