---
title: "cat: /proc/asound/cards: No such file or directory"
date: 2010-09-11
forum: Hardware
---

### Post by roadcone on 2010-09-11
So... Since that awful audiopulse update, I've been trying everything to get sound working with flash. One or a combination of things I've tried has nuked my system and now:

```
cat: /proc/asound/cards: No such file or directory
```

I'd like someone to help me get my audio working, because now no sound card (this is integrated, not even USB) is detected and I have no sound at all.

---

### Post by Æon Flux on 2010-09-11
> **roadcone said:**
> So... Since that awful audiopulse update, I've been trying everything to get sound working with flash. One or a combination of things I've tried has nuked my system and now:

```
cat: /proc/asound/cards: No such file or directory
```I'd like someone to help me get my audio working, because now no sound card (this is integrated, not even USB) is detected and I have no sound at all.


join #alsa on freenode ask them there if your card is supported if it isnt join #oss and ask them too. if still no joy you will have to change sound card.

99% of sound cards are supported by alsa driver so usually u should get some sound if you dont hear anything it can be cuz the driver is missing or your card isnt supported



to check up if your card is recognised type in terminal aplay -l

to check up what card you have got even if it isnt supported type in terminal lspci

---

### Post by roadcone on 2010-09-11
My sound card is certainly compatible. ALSA and audiopulse were working, it just isn't now.

---

