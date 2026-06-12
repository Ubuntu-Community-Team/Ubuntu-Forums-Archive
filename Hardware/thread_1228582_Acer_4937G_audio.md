---
title: "Acer 4937G audio"
date: 2009-08-01
forum: Hardware
---

### Post by craftomaniac on 2009-08-01
Hello everyone.

I'm about to switch from my old laptop (Acer Travelmante 6292) to this new laptop (Acer Aspire 4937G). 

I've already installed Ubuntu Jaunty and am already halfway through configuring everything to the way I like, but I just realized that the sound doesn't really work.

Playback is fine, except that when I plug in my headphones, sound plays through the headphones but Ubuntu does not automatically cut sound to the speakers. The "Headphones" checkbox does not change anything.

Input from the built-in mics does not work at all. Changing any of the mic boost options only adds noise to the speaker/headphone output. When I plug in a random microphone, it works, but is very noisy as well. 

This laptop's audio card is the Realtek ALC888.
I've already edited the /etc/modprobe.d/alsa-base to include
options snd-hda-intel model=acer but nothing seems to have changed.
I've also tried fiddling with all the volume mixer controls but none of them fix the audio input issue.

Interestingly, when I try to record in audacity (aside from the silence from the non-working input options, when I up the mic boost controls (to get noise), there is only noise on the right channel of the stereo audio recorded.

Does anyone know of a way to solve this problem?
Thanks in advance.

---

