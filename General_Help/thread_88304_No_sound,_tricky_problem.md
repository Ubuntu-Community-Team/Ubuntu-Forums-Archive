---
title: "No sound, tricky problem"
date: 2005-11-09
forum: General Help
---

### Post by phoenixy on 2005-11-09
All right, I'm running out of idea, please help :) 

Running 5.10 on a Gateway MX7515 laptop. Sound card works in Windows, and the driver there shows 
Conexant CX20468-31 audio driver Ver 6.14.10.0585

In ubuntu, lspci shows
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 02)

lsmod shows
snd_atiixp               18912 1
snd_ac97_codecs     72188 1 snd_atiixp
snd_pcm_oss           46368 0
snd_mixer_oss          16128 1 snd_pcm_oss
snd_pcm                 78344 3 snd_atiixp, snd_ac97_codecs, snd_pcm_oss
snd_timer                21764 1 snd_pcm
snd                        48644 8 snd_atiixp, snd_ac97_codec, snd_pcm_oss,snd_mix_oss,snd_pcm,snd_timer
soundcore                9184 1 snd
snd_page_alloc         10120 2 snd_atiixp, snd_pcm

So, it seems to me like Gnome thinks it had picked up the sound card. Under Sound Preference, "ATI IXP" is listed as my sound card

Any idea?

---

