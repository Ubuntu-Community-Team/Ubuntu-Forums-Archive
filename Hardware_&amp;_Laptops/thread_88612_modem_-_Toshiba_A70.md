---
title: "modem - Toshiba A70"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by ivanp on 2005-11-10
Hi I've been checking this forum and it seems to be more usual the sound not to work on toshiba laptops. It does work on mine, but my problem is the modem: It cannot be detected by the system. I'm running breezy 5.10. The output for ls mode is as follows on the sound and modem section. It is listed so I might guess it's just a matter of proper configuration, but I'm just guessing. I'm very newbie

snd_atiixp_modem       15396  0
snd_atiixp             18912  1
snd_ac97_codec         72188  2 snd_atiixp_modem,snd_atiixp
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_p cm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  9 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_p cm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  3 snd_atiixp_modem,snd_atiixp,snd_pcm

thanks in advance

---

