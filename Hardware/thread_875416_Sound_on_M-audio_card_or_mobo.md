---
title: "Sound on M-audio card or mobo"
date: 2008-07-30
forum: Hardware
---

### Post by jerrywo on 2008-07-30
Hmmm, on Rhythmbox, my sound comes out my sound card jack (M-Audio revolution 5.1)

On BBC and/or web content, my sound comes out my motherboard jack (as does the Ubuntu start-up theme).

My lsmod | grep snd reads:
snd_ice1724            92264  2 
snd_ice17xx_ak4xxx      5120  1 snd_ice1724
snd_ac97_codec        101028  1 snd_ice1724
ac97_bus                3072  1 snd_ac97_codec
snd_ak4114             10752  1 snd_ice1724
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_hda_intel         344728  2 
snd_hwdep              10500  1 snd_hda_intel
snd_pcm                78596  5 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss,snd_hda_intel
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_pt2258              5504  1 snd_ice1724
snd_i2c                 6528  2 snd_ice1724,snd_pt2258
snd_ak4xxx_adda         9472  2 snd_ice1724,snd_ice17xx_ak4xxx
snd_seq_dummy           4868  0 
snd_mpu401_uart         9728  1 snd_ice1724
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_rawmidi            25760  2 snd_mpu401_uart,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  26 snd_ice1724,snd_ac97_codec,snd_ak4114,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_hwdep,snd_pcm,snd_pt2258,snd_i2c,snd_ak4xxx_adda,snd_seq_dummy,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

I would, of course like ALL my sound to come out the M-audio card output!
Sounds like some sort of config mess-up
any hints?

Running 8.04
Jerry W

---

