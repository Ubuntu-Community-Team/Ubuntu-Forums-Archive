---
title: "ALSA - More than 4 sound cards?"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by CheetahCat on 2006-10-14
Hello fellas,

I'm trying to set up a music server for my home. It's a simple machine with 6 PCI sound cards plugged in and I'm using ALSA as sound system.

The first 4 PCI sound cards get recognized just fine but card 5 and 6 don't work, seems as if ALSA does not know that they are there.

What do I do to make the remaining two cards work?

Thanks in advance!

~ Cheetah

---

### Post by SoloSalsa on 2006-10-14
I really wouldn't know, but are they all supported cards?  Like, being installed in a different order would still prevent support?
I am truely interested in what you are doing.

---

### Post by CheetahCat on 2006-10-15
> **SoloSalsa said:**
> I really wouldn't know, but are they all supported cards?  Like, being installed in a different order would still prevent support?
I am truely interested in what you are doing.

I'm using 6 cards which work with the snd-cmdpci driver. It just seems that the hardware detection script does not find more than 4 cards.

What I'm doing is to set up a server box in the basement and centrally control speakers in all rooms of the house using mpd (Musicplayer Daemon).

~ Cheetahcat

---

