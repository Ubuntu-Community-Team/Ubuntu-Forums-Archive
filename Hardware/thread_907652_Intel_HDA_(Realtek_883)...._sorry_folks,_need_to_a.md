---
title: "Intel HDA (Realtek 883).... sorry folks, need to ask..."
date: 2008-09-01
forum: Hardware
---

### Post by KhipuX on 2008-09-01
The problems with Intel HDA sound just seem to be never ending. I have now read and tried more than 40 solutions regarding 'quiet' sound on this chipset over the last 12 months and still don't have any success. Even recompiling with several different options hasn't changed my situation. It's not that the sound doesn't work, just it's very quiet even with all the mixer channels on 100, the FRONT and PCM settings played around with and the output hardware changed twice.

My sound is onboard, several members have suggested buying a soundcard but I only have Creative Labs stuff available in Ecuador where I live. I haven't been able to use Skype or listen to any music while I've been working just because of this sound problem. OSS4 works well but it doesn't like some of my apps and I outright refuse to keep updating the darned driver every six months. Buying a license is out of the question - the OSS4 website doesn't accept credit cards from Ecuador.

So, is ALSA going to get this sorted out once and for all or does anyone know where I can grab a solution that works? I have an Intel 945GN (ICH8 Realtek 883/888 sound chips) motherboard. If you have the same and know a solution please post it on here, 12 months is a long time to keep hacking away on this.

Thanks all.

---

### Post by KhipuX on 2008-09-01
Sorry, forget to mention I'm on Kubuntu 8.04.1. I have upgraded ALSA to 1.0.17 but it is reversable.....

---

### Post by jsundqui on 2008-09-08
I'm having all sorts of similar problems after upgrading from 7.10 to 8.04

It worked flawlessly in 7.10.

Is it possible to downgrade to the 1.0.14 alsa driver that was in 7.10?

Sound actually sounds great if I boot 8.04 into the old kernel that shows up in the boot menu (2.6.22-15) rather than the newer one (2.6.24-19).  Now before everyone says just boot there, I have problems with X there.  But who knows, that may be easier to solve than these sound problems.

My problems are the quietness mentioned, and also getting accurate surround sound playing under mythtv (rear channels are too soft, even after playing with alsamixer).

---

### Post by KhipuX on 2008-11-25
I've had this problem with all the Intel boards of used since 6.10. I've now tried everything I can find on the net and still have quiet sound. I live in South America and trying to find sound cards here is next to impossible. Mind you I did find a Creative Audigy card the other day for USD$210.

So, free operating system, most common chipset on Earth and it's still going to cost me over $200 to get sound. Can someone tell me where I can buy a cheap Atari ST from in Ecuador because it worked much better than this?

---

