---
title: "MacBookPro5-5 ALSA distortion"
date: 2009-12-28
forum: Hardware
---

### Post by craftomaniac on 2009-12-28
Hey everyone.

I've been using Ubuntu for quite awhile on my MBP. I've only recently found the time to upgrade to Karmic and it works fine, except that I found that there is always distortion when I try to use ALSA.

In Jaunty, I was able to use ALSA-loving applications like LMMS and QSynth without any such problems, but now there seems to be distortion when I use JACK (which outputs audio to ALSA?) and same with LMMS. If I select PulseAudio in LMMS, the sound outputs fine but as with all things PulseAudio, there is high latency.

I've tried both solutions outlined in [https://help.ubuntu.com/community/MacBookPro5-5/Karmic](https://help.ubuntu.com/community/MacBookPro5-5/Karmic). Installing linux-backports-modules-alsa-karmic-generic gives good sound in PulseAudio but distortion in ALSA, not installing anything gives no sound, and installing from source detects the Cirrus sound card but does not detect the audio controls (thus no sound).

I don't really have much experience troubleshooting ALSA issues and I don't know where to start.

Is there any way this problem can be solved (for me and all other MBP users)? Karmic works perfect except for this slight regression. I would really like to be able to continue to use LMMS/Ardour/JACK to create audio on Ubuntu. Thanks in advance.

---

