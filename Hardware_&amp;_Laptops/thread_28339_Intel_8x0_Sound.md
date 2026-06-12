---
title: "Intel 8x0 Sound"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by locque on 2005-04-19
I have searched through these forums as thourough as I could and have not been able to solve my problem. I can't get any sounds out of my laptop. It is a Gateway 4520GZ. The following is the output of lsmod|grep snd:

snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  9 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

That is with XMMS running and playing music, but nothing coming out of the speakers. ALSAMIXER is unmuted and I don't get any errors, it just simply won't output any sound. It thinks that it is, hence XMMS playing music, but no sound comes out....

---

### Post by burlap on 2005-04-20
Have you tried changing output plugin from alsa to esound (libesd)? (Preferences -> Audio I/O audio plugins). I have also intel 8x0 and no alsa works, but esd is doing fine (in xmms, vlc).

---

### Post by locque on 2005-04-20
Yep...tried it. I'm thinking that it is somekind of hardware volume control of some sort.... It is really frustrating though... It thinks that it's playing but the hardware isn't working...

---

