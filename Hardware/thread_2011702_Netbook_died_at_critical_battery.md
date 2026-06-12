---
title: "Netbook died at critical battery"
date: 2012-06-27
forum: Hardware
---

### Post by AnotherMuggle on 2012-06-27
I regularly use hibernate on my HP Mini 210 and have never had an issue with it.  When Ubuntu starts moaning the battery is low I ignore it till it gets too low and hibernates.  This evening it didn't hibernate, the machine just abruptly powered off.

There used to be a key which could be changed via gconf-editor to change the critical level of the battery.  Is there something similar in 12.04?

Cheers,
TK

---

### Post by AnotherMuggle on 2012-06-30
The battery just reached critical again and I ignored it as long as I could allow myself.  It got a lot lower than I would normally allow it to so I plugged it in to the mains.  I was curious to know if it would hibernate but I decided it's not worth the expensive of a new battery.  I already met that fate once in the past and don't fancy going there again.

Anyway the point of this post is to note that hibernate at low battery appears to have stopped working in the last few weeks and I'd like to learn why.  Manual hibernation and resume works perfectly every time so I'm suspecting the problem is with detecting the low battery level.

---

### Post by AnotherMuggle on 2012-06-30
Apparently this isn't a very popular thread but incase anyone stumbles across it looking for answers, it looks like much of the functionality I was familiar with in gconf-editor is now part of dconf-editor.  You need to install the dconf-tools package.

I have increased the battery critical level warnings and action times to see if that helps.

---

### Post by David Andersson on 2012-06-30
[QUOTE=AnotherMuggle]I regularly use hibernate on my HP Mini 210 and have never had an issue with it.  When Ubuntu starts moaning the battery is low I ignore it till it gets too low and hibernates.  This evening it didn't hibernate, the machine just abruptly powered off.[/QUOTE]

The capacity of the battery slowly decays(*) with time. Maybe it has reached a point where, at the set threshold, there is not enough energy to complete a hibernation.

[QUOTE=AnotherMuggle]I have increased the battery critical level warnings and action times to see if that helps.[/QUOTE]

Please feel encouraged report your findings. Maybe someone will read.

(*) (or decreases, or drops off. Thanks, synonyms at merriam-webster)

---

