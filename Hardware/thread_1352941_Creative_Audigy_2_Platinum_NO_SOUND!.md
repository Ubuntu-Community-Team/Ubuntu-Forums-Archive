---
title: "Creative Audigy 2 Platinum NO SOUND?!"
date: 2009-12-12
forum: Hardware
---

### Post by Cforcer on 2009-12-12
I'm new to Ubuntu, but I'm experienced user on other systems & I've never have problems with my sound card.... System seems fine & recognizes my sound card, but no sound is coming from speakers... Please help me...

[B]sudo lsmod | grep snd
snd_emu10k1_synth       6140  0 
snd_emux_synth         32860  1 snd_emu10k1_synth
snd_seq_virmidi         5628  1 snd_emux_synth
snd_seq_midi_emul       6332  1 snd_emux_synth
snd_emu10k1           135232  20 snd_emu10k1_synth
snd_ac97_codec        101216  1 snd_emu10k1
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75488  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9252  2 snd_emu10k1,snd_pcm
snd_util_mem            4156  2 snd_emux_synth,snd_emu10k1
snd_hwdep               7200  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      6940  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                50224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  21 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6920  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  33 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd


& it's not muted....!!!
[/B]

---

