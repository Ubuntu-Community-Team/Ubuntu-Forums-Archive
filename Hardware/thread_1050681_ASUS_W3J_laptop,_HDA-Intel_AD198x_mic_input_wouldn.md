---
title: "ASUS W3J laptop, HDA-Intel AD198x mic input wouldn't work"
date: 2009-01-25
forum: Hardware
---

### Post by johnhamster on 2009-01-25
Hi, I'm running ALSA 1.0.17 on my Kubuntu 8.10, 32 bit, which in turn runs on my ASUS W3J laptop with HD-Audio Intel card that is identified as AD198x. In most of the settings for alsa-base I get situation 1) sound output working, but no sound input. The only time when sound input seems to work is with the 2) "options snd-hda-intel model=3stack", but then, ironically, sound output stops working. My laptop has only two jacks (one for microphone, one for headphones). What should I use for a "model" (tried a lot of variants, much gave me situation 1) or, perhaps, what's the alternative resolution of the problem? Here's where you can find the output of my alsa-info.sh - [http://www.alsa-project.org/db/?f=aab2e420b267e59c9f7d6d77c645ed1d79359e35](http://www.alsa-project.org/db/?f=aab2e420b267e59c9f7d6d77c645ed1d79359e35)  Also, I believe it's most likely not a volume level issue. Thank you!

---

