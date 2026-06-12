---
title: "no sound Realtek ALC260 @ ATI SB450 - High Definition Audio Controller"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by robotlover on 2006-11-27
I installed new Ubuntu 6.10 on my laptop HP B1900, but no sound at all, although the sound card seems to have been recognized. Now I have turned the mixer volumes to be 100%, still no sound. I also have 
tried installing the latest alsa driver and realtek sound driver, neither is useful, please do me a favour, thank you very mucn.

uname -a
Linux liu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.12_r4.05.
Compiled on Nov 26 2006 for kernel 2.6.17-10-generic (SMP).

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0500000 irq 209

cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC26

lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

content of /etc/modules:
lp
sbp2

---

### Post by MadeR on 2007-01-01
[http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260](http://ubuntuforums.org/showthread.php?t=324764&highlight=alc260)

---

