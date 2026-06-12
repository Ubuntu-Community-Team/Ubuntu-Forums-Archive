---
title: "No sound capture on laptop Edgy install"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by drpaul on 2007-02-03
I have recently installed and updated Edgy on my HP dv6150us laptop. It has an Intel Core 2 chipset [processor, video, sound]. I've got most things working, but I get nothing from sound capture on the builtin microphone.

I've tried all three options on the sound capture setup: generic HDA, Alsa, OSS.
The Test button generates a very quiet, low frequency remble from the speakers.

Any ideas will be appreciated.

Paul

---

### Post by drpaul on 2007-02-20
For anyone interested.

Solved by installing a newer version of the Alsa driver [...13].

Fixed capture and put sound on the earphone jack, but didn't turn off speakers when earphones are plugged in.

Paul

---

