---
title: "Soundblaster AWE 32 not working"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by OMRebel on 2006-04-14
How do I get this setup and working in Breezy?  Whenever I go to the volume control, it tells me, "No volume control elements and/or devices found."

Please help.

---

### Post by xolot1 on 2006-04-14
it took me a while to figure out sound as well.
i think i have an AWE 32 as well.

after a bunch of searching, i found this, and i think it was the key i was missing.

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

looks like
snd-sbawe= SoundBlaster 16,32,64 AWE
is the module you want.

---

