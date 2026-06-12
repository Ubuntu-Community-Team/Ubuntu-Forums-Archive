---
title: "ASUS M2R32-MVP 's coaxial digital output issue"
date: 2009-10-12
forum: Hardware
---

### Post by josarn on 2009-10-12
When closing a session in gnome and starting a new one I keep losing the sound from the digital coaxial output only . I stumbled upon the fact that opening  
"Aplications > Sound > PulseAudio Volume Control" gets the sound back and remains so while the application is open. No muted channels in Alsamixer.
The relevant part of /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=6stack-dig
```Is there someone with the same motherboard that can confirm this behavior?

---

