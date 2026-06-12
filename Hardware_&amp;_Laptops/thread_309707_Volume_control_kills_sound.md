---
title: "Volume control kills sound"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by straxus on 2006-11-30
I have a fresh install of Edgy on an Asus A8Js.  Sound works fine until I try to adjust the volume, at which point it goes silent, and won't return unless I reload /etc/init.d/alsasound.  I compiled and install the latest version of ALSA (1.0.13) but still have the problem.

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

lsmod | grep snd
snd_hda_intel          23320  1
snd_hda_codec         222336  1 snd_hda_intel
snd_pcm_oss            56320  0
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                93444  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26628  1 snd_pcm
snd                    70672  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

---

### Post by straxus on 2006-12-01
I've also just discovered that when I plug in speakers or headphones, all the sound comes from the right speaker.  The BIOS boot noise comes from both sides, so it must be a driver issue.  Any ideas guys and gals?

---

### Post by straxus on 2006-12-03
Found the fix. Added the following line to /etc/modprobe.d/alsa-base

*options snd-hda-intel position_fix=1 model=3stack*

---

