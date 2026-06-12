---
title: "Compac Mini 110 - No sound/micro with Skype"
date: 2009-09-05
forum: Hardware
---

### Post by Tedi on 2009-09-05
Hi,

I manage to partially solve the issues with the sound. Now sound is working with headphones but not speakers.

Anyway, sound seems to work for all applications but not for Skype. Microphone is neither working.

Any suggestion?

Thanks

---

### Post by PhilMize on 2009-09-08
I have the sound working, But still no mic for skype either... I hear 9.10 it works just fine so I don't mind waiting...

---

### Post by rtb on 2009-10-25
> **PhilMize said:**
> I have the sound working, But still no mic for skype either... I hear 9.10 it works just fine so I don't mind waiting...

Actually, I was having problems with the mic on an HP Mini 110, even with 9.10, up until today (24-Oct-2009).  The only solution I'd found was to compile and install ALSA 1.0.21 by hand.  

However, this appears to be related to [bug #458302]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/458302") on launchpad.  I installed the linux-backports-modules-alsa-karmic package, and the mic started working again.

---

