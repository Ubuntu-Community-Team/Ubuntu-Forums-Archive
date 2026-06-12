---
title: "Anything sent to /dev/dsp is all crackly!"
date: 2006-03-26
forum: Hardware &amp; Laptops
---

### Post by dmb on 2006-03-26
Hello, I use intel 915g built in sound card alsa modules:
snd_hda_intel          15872  4
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  2 snd_pcm_oss
snd_pcm                78344  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer

And anything thats gets sent to /dev/dsp (OSS compatibility which still many programs send sound to) is always crackly, and sounds crappy. Anything that uses also libs, works fine. Is there any solutions on how to fix this? I use audicity, and its essential that i get good sound quality when producing. Thanks.

---

### Post by dmb on 2006-03-28
*bump*
Does it happen to have to do with a mismatch in frequencies?

---

### Post by dmb on 2006-03-30
*bump*

---

