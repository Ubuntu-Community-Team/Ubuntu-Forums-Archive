---
title: "No sound with horay release"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by artimess on 2005-04-09
I installed Hoary release, evrything works fine but sound.  I made sure that the speakers are unmuted;  Still no sound;  here is my lsmod | snd, do appreciate any hints to fix this problem.
Artimess
artimess@ubuntu:~$ lsmod | grep snd
snd_atiixp             22880  2
snd_ac97_codec         83472  1 snd_atiixp
snd_pcm_oss            56608  1
snd_mixer_oss          20288  2 snd_pcm_oss
snd_pcm                99020  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_timer              26248  1 snd_pcm
snd                    58728  6 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11424  3 snd
snd_page_alloc         11464  2 snd_atiixp,snd_pcm

---

### Post by Suvarin on 2005-04-09
[QUOTE=artimess]I installed Hoary release, evrything works fine but sound.  I made sure that the speakers are unmuted;  Still no sound;  [/QUOTE]

Did you do check if the speakers were muted or if the sound was muted in the Gnome Volume Control? For some soundchips sound is muted on install (I belive it is a known bug). Open the volume control (in the notification area on the upper right) and make sure that *Master*, *PCM* and *PC Speaker* channels are all unmuted.

Thats all ideas I have at this moment.

---

### Post by Gyom on 2005-04-09
I did as you recommended, it works fine! Thanks

---

