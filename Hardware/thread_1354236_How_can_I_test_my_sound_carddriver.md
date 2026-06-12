---
title: "How can I test my sound card/driver?"
date: 2009-12-13
forum: Hardware
---

### Post by dizzy1kenobi on 2009-12-13
I have no sound with YouTube, VLC, Audacious.

My laptop had a hard time with a restart last nite and actually froze forcing me to manually shut it down.  When I turned it on this morning I had no sound.

I did check the sound preferences to make sure nothing was muted.

---

### Post by lloyd_b on 2009-12-14
> **dizzy1kenobi said:**
> I have no sound with YouTube, VLC, Audacious.

My laptop had a hard time with a restart last nite and actually froze forcing me to manually shut it down.  When I turned it on this morning I had no sound.

I did check the sound preferences to make sure nothing was muted.

In a terminal window, type "aplay -l".  If the sound card is working and a driver loaded for it, this will display it.

It this responds with "no sound cards found" or something similar, then there's either a driver problem or the sound hardware is dead.  At that point, run "lspci" in a terminal window, and see if the sound hardware is listed in there.

Lloyd B.

---

