---
title: "Bad sound quality..."
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by WeberMax on 2005-04-13
Hello, i have the problem that videos, mp3s,oggs,... sounds like 16kb/s also in very bad quality. When i turn up the volume in gnome that it begins to whistle. :( 

Hardware: SB Live! EMU10k1

lsmod says:
emu10k1_gp              3840  0
gameport                4608  1 emu10k1_gp
snd_emu10k1            81668  2
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9824  3 snd

Hmm, please help  :smile: 

regards

---

