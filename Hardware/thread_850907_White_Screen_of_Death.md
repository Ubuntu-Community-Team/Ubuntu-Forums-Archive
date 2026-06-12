---
title: "White Screen of Death"
date: 2008-07-06
forum: Hardware
---

### Post by Naeem Firdous on 2008-07-06
while using firefox system suddenly goes white screen and only way out of this is to restart. i am not sure whats going on behind that white screen.

i checked the system log, this is what i got there:

pulseaudio[5952]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
pulseaudio[5952]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
pulseaudio[5952]: alsa-util.c: Cannot find fallback mixer control "Mic".



dont understand whats causing this problem, i have seen this for few days now. Firefox 3 , Hardy heron 8.04

any suggestions will be helpful.

---

### Post by DJ-Dark on 2008-07-06
It has to do with your sound, if you are going to a website with sound ALSA is trying to change your settings to be louder than what you have them set at.

---

