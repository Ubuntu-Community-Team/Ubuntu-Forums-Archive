---
title: "clicking noises with audigy 2 nx"
date: 2006-03-19
forum: Hardware &amp; Laptops
---

### Post by beatgeek on 2006-03-19
I have the USB Audigy 2 NX sound card for my laptop, and no matter whether I use OSS, ALSA, or ESD, I get weird clicking noises that fade in and out of any audio, in any program. I'm using Breezy, and this doesn't happen in Windows. I can get the sound to work if I tell it to use my laptop's built-in sound, but that means I have to listen to it on my crappy laptop speakers, which isn't a more appealing option than annoying noises on nicer speakers. Any suggestions?

---

### Post by RJA on 2006-05-24
It's because the soundcard doesn't really support 44.1khz audio.  It resamples it up to 48khz - I can't help you in Gnome, but under KDE you'd go K -> System Settings -> Sound & Multimedia -> Hardware -> Use custom sampling rate.

Should at least put you in the right direction :).  If it isn't anywhere obvious in Gnome, then you'll need to do a little searching for .asoundrc and change it over in there.

---

