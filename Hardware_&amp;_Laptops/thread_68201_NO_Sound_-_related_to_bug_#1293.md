---
title: "NO Sound - related to bug #1293?"
date: 2005-09-22
forum: Hardware &amp; Laptops
---

### Post by thezerogroup on 2005-09-22
Hello all!

My sound card is not working! I believe my problem is relating to bug#1293. 

If I go to SYSTEM->PREFS->Multimedia System Selector

I see under audio the following choices:

ALSA
Artsd
ESD
OSS
Custom 

I select ALSA and then click test and get the following error message:
"Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'"

I then go to command line and type

#esd
ALSA lib pcm_dmix.c:868: (snd_pcm_dmix_open) unable to open slave

---

### Post by thezerogroup on 2005-09-22
Failed to mention my sound card is a REALTEK intagrated sound card on a Sony Vaio VGN-S470p

---

