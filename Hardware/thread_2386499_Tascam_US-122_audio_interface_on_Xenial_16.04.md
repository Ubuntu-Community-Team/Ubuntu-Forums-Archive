---
title: "Tascam US-122 audio interface on Xenial 16.04"
date: 2018-03-06
forum: Hardware
---

### Post by rooker2 on 2018-03-06
Hello :)

I'm trying to get my Tascam US-122 audio/midi interface to work on Xubuntu Xenial 16.04.3 (64bit).
I remember that it worked with older Ubuntu versions like a charm - including jackd.

But now, I cannot access the device anymore (neither pulse, nor aplay/arecord or jackd) :(
I've followed [the tutorial on ALSA.opensrc.org]("https://alsa.opensrc.org/Tascam_US-122"), and the alsa-firmware (v1.0.29) loads (green light on the device), and /proc/asound/{cards|devices|modules} all list the USX2Y device properly.

But when I try to do anything with that alsa device, I either get "Broken pipe" or "Unable to install hw params" or some other error like this.

Seems like all applications are trying to tell me in their own words that some part of my setup is faulty ;)


I've probably read all articles I could find on the web about this, but they either refer to older Ubuntu distros, or the US-122L (which's setup is completely different).

Has anyone managed to get the US-122 running on a recent version of Ubuntu/Debian?
Thanks in advance! :D

---

