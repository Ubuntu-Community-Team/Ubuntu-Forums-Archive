---
title: "Looking into buying a compatible screen adapter that support dual monitors"
date: 2008-07-07
forum: Hardware
---

### Post by dirkhaim on 2008-07-07
I am looking into buying a screen adapter that supports a dual monitor setup. Since my hardware supplier can't tell me if a certain card will be totally compatible with Ubuntu, I have to find it out myself before ordering one.

Basically, I am looking for a pretty basic adapter. I am a developer and the computer used for programming only. Can anyone recommend a simple adapter that is both widely available and will provide me 100% compatibility?

Thanks

---

### Post by dirkhaim on 2008-07-08
Anyone?

Or can you point to where I can actually ask this question?

---

### Post by molochi on 2008-07-08
If by "screen adapter" you mean video card, most of the 7xxx series of Nvidia Geforce cards with 2 analog capable ports running the propietary NV driver seem pretty easy to set up with dual monitors. As easy as windows anyways. They're pretty inexpensive too. The only issue I've run into is trying to get some cheap "HDTV"Monitors (olevia), that report the wrong native resolution, to work.

Also, Matrox offers an analog external box (dualhead2go triplehead2go)that plugs into a regular vga port and makes multiple monitors act like a single one for a single video card. Not as cheap. 0% support from Matrox. But it works with a relatively simple option entry in xorg.conf (no drivers needed) off of integrated graphics on a notebook. The card still has to support the combined resolution, but most integrated cards will still do 2560x1024 at least. I had one (a dualhead2go) linked to a KVM and 3 systems. Worked like a charm.



As for 100% support, it's easy, it just requires a tech with patience, a blank check and no time limit.

---

### Post by dirkhaim on 2008-07-09
Thanks. I guess I will for some of the lower end 7xxx series cards

---

### Post by Qinjuehang on 2008-07-09
I wouldn't recommend that, since the 8600GT can cost a bit more than 50USD...its a cheap deal, and would even get you decent 3D acceleration (compiz!). The "NV" driver would work, but it is unstable, and I wouldn't reccommend it. You can easily setup dualview using the Nvidia proprietary drivers, like I sometimes do with my TV. Also a 8600GT would be more future-proof, since OSes are just getting more and more bloated with 3D effects.

---

### Post by geogur on 2008-07-11
i have an older pc that dose 2 heads fine running ubuntu 7.10 but now i can only clone screens with ubuntu 8.0 i even trashed my upgrade went back to 7.0, 2 heads. do the up grade 1 head on 2 monitors. i two need a new vidio card!

---

