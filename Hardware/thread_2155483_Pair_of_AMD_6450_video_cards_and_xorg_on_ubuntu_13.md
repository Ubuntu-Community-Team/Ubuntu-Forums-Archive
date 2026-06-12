---
title: "Pair of AMD 6450 video cards and xorg on ubuntu 13.04"
date: 2013-06-18
forum: Hardware
---

### Post by egandt on 2013-06-18
I have a pair of 6450's (1 16x and 1 1x PCIe), in a workstation (HP) now I can not boot into X using the default open source drivers as it always segfaults on glibc, however if I remove 1 card (either card) it works fine.  The problem here is I have 4 screens (hence 2 cards), I do not need 3D or anything so the AMD drivers are overkill (and I might mention unstable as flgrx is responsible for 90% of the crashes I've seen on ubuntu 13.04), however while the open source driver finds both cards it does not work at all, any thoughts as to why, I can not be the only person with a pair of AMD cards that wishes to use the default drivers that come with Ubuntu?  

I can upload the failure, if people want, but for now this is a more general question.  Does this work for anyone, is it possible with out using the Binary drivers?  If so how?

Thanks,
ERIC

---

### Post by mdmcaf on 2013-06-18
I know that running dual cards in Linux can be a bit tricky, especially with the poor support that AMD cards have on Linux systems. Would you be able to swing getting a single card that can handle 4 monitors? I remember way back in the day when I was messing around with four monitors on two cards it took quite a bit of tweaking xrandr in order to get them to work and there were updates that liked to kill the configuration and in the end I decided that I was spending so much time trying to fix what the updates killed that the impact on my productivity wasn't worth having 4 monitors. Granted, that was about 10 years ago...hopefully things have changed.

Anyways, I think that your best bet would be to just get an old high-end video card (I'm running three monitors on an XFX Radeon 6870) that has enough outputs to be able to handle 4 monitors. Sure, it costs a bit of money...but I think you'll be saving yourself a lot of headaches.

---

