---
title: "Sound system breaks in newest kernel (2.6.24-17)"
date: 2008-05-26
forum: Hardware
---

### Post by onlineapps on 2008-05-26
When running 2.6.24-17 on the radeon driver for my Radeon x300 card on Kubuntu 8.04, my sound goes splat. The Twinkle SIP client says:

Cannot access the ring tone device (ALSA: default).
Cannot access the speaker (ALSA: default).
Cannot access the microphone (ALSA: plughw:1,0).

Additionally, the KDE sound system breaks. Finally, jockey-kde gives:

ERROR: could not open /proc/asound/cards: [Errno 2] No such file or directory: '/proc/asound/cards'

I reinstalled the Pulse libraries, alsa-base, and all the other sound libraries Adept showed. Nothing worked.

---

