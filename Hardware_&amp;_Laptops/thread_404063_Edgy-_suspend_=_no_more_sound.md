---
title: "Edgy- suspend = no more sound"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by stormchas3r on 2007-04-07
I have a Thinkpad R51 which runs perfectly until now.  I tried to suspend my laptop a few times, and now I have no sound for anything ie. login, system sounds or even music.  I reinstalled alsa and still no sound.

Has anyone had this issue, or know how to fix this?

Ty

---

### Post by acrowde6 on 2007-04-09
I had the same problem with my ThinkPad T21.

To solve this I went to the mixer. (Go to console and type *alsamixer* and make sure that all the devices are unmuted) In my case, the DAC was turned to 0. I turned it up and the sound worked fine again. Hope this helps.

---

