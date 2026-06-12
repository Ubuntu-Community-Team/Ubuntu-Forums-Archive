---
title: "Speaker/mic issues on Vostro 1320"
date: 2009-07-11
forum: Hardware
---

### Post by kredei on 2009-07-11
I've got everything working beautifully on my new Vostro 1320, except for two issues: 1) the laptop's built-in speakers don't mute when I plug headphones in; 2) the webcam's microphone doesn't work/isn't recognized by Skype or any other software I've tried, and even plugging an external mic into the jack results in just a recognizable but seriously distorted sound. It seems like the second is a reported bug at least for the 1720 ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/386858](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/386858)) but I haven't found anything on the first. Any ideas on workarounds for either?

---

### Post by DJDANG on 2009-07-30
Hi there!
I have the same problem, the speaker-headphones switch doesn't work and the webcam microphone is not recognized. Can anybody help us here please?!!!
thanks,
Daniel

---

### Post by cmreigrut on 2009-08-11
Looks like the former is solved in karmic:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382836](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/382836)

---

### Post by kredei on 2009-08-12
Thanks! Upgrading to Alsa 1.0.20 fixed both issues.

---

### Post by cmreigrut on 2009-08-13
Well, I've upgraged to alsa 1.0.20, which has fixed the internal microphone problem, as well as the speaker switch!  Unfortunately, it has also now set the headphones to barely audible, even at full, which makes the headphones rather useless.  Am I the only one?

---

