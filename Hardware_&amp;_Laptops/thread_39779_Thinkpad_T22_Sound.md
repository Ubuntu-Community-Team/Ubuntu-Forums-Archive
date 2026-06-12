---
title: "Thinkpad T22 Sound"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by chrisw on 2005-06-06
Hi There

I am having difficulty getting sound working on my T22....  I have found a number of similar request on the board but no real answers.

Has anyone got the sound working on a T22 and if so, how did you manage it ??

---

### Post by JLB on 2005-06-11
I own a t22 and have been running ubuntu since warty came out. running hoary now. sounds just works. Is your speaker volume turned on? press the volume buttons (upper left on keyboard) a few times too.

lscpi output for the sound card on my t22 is :

0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

lsmod output for the sound card on my t22 is :

snd_cs46xx             80328  1
snd_rawmidi            22944  1 snd_cs46xx
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_cs46xx
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  10 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_cs46xx,snd_pcm
gameport                4608  1 snd_cs46xx

---

