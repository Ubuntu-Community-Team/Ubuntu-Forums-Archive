---
title: "amarok sound quality problem"
date: 2008-07-14
forum: General Help
---

### Post by robitor on 2008-07-14
The sound quality in Amarok is terrible, the bass just isn't there. When i play my music in banshee (the same files) the bass is full and the whole sound is ALOT better. 

I've heard amarok is the best, but how can it be when the sound quality is so bad? It might be something wrong with how amarok is set up, can someone help me out?

---

### Post by bingoUV on 2008-07-14
Tools -> Configure Amarok -> Engine -> Output Plugin.

Change this to what suits you good. Pulse audio works fine for me.

---

### Post by robitor on 2008-07-14
that doesn't work, i get an error message: Audio output unavailable; the device is busy.
xine parameters:

---

### Post by Roasted on 2008-07-15
What are you set up with? Alsa? Or did you install PulseAudio?

---

### Post by cyclobs on 2008-07-15
there is an equliser on amarok which is default off

find it in tools-->equliser

---

### Post by bingoUV on 2008-07-15
> **robitor said:**
> that doesn't work, i get an error message: Audio output unavailable; the device is busy.
xine parameters:

What doesn't work? 
1. Setting it to pulse audio? 
2. or selecting any output plugin doesn't work? 
3. Which output plugins are listed in your amarok?

---

