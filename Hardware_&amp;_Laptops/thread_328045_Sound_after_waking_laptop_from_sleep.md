---
title: "Sound after waking laptop from sleep"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by catfox on 2006-12-30
hi all,
i've got a sony vaio fe-28H laptop which has an integrated intel sound card (using snd_hda_intel module). the laptop sleeps perfectly, but when it wakes up again, if i try to play a sound, even a 3 second wav, it plays for ever with lots of jumps and scratches in it.
basically, i can only have the laptop usable after a sleep if i reboot it.

i've tried restarting the alsa-utils service after a sleep, but this had no effect.
i've also tried unloading the snd_hda_intel module, but i'm told its busy and cant be unloaded.

any ideas what i can try next?

cheers

---

