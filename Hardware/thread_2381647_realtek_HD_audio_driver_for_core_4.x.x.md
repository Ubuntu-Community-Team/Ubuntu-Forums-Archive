---
title: "realtek HD audio driver for core 4.x.x"
date: 2018-01-03
forum: Hardware
---

### Post by calibal on 2018-01-03
Hello :)

I have an asus transformer T102HA, i have installed ubuntu 17.10 on it.
But i have no sound.

I've tryed to update the core to lastest stabe release available (with ukuu) but no way.
alsa-utils, and alsa-base are installed too, but the sound cord is not reconised and alsamixer told me there is no command found for this card.


On realtek website there are some drivers, but so old, for core 2.6 and 3.x.x.

Is someone know how i can solve this issue ? 

thanks by advance :)

---

### Post by Yellow Pasque on 2018-01-03
This might be relevant: [https://bugs.freedesktop.org/show_bug.cgi?id=100488](https://bugs.freedesktop.org/show_bug.cgi?id=100488)

> On realtek website there are some drivers, but so old, for core 2.6 and 3.x.x.

No, don't use those. The appropriate driver is already found in the kernel.

---

### Post by calibal on 2018-02-05
i do not understand, i have tested with ubuntu mate 17.19 and the sound was working well (but not touch, pad, and so on ...)
but when i install unbuntu 17.10.1 all is working except the sonud.

it does not reconise the Audio [Intel HDMI/DP LPE Audio], périphérique 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio] 

it should be the same core, then why one is working and not the other ?

---

