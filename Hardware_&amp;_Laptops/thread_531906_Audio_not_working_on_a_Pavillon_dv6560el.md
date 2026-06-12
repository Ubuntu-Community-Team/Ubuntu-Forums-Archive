---
title: "Audio not working on a Pavillon dv6560el"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by drf_av on 2007-08-22
Hi everyone,
I just bought a new pavillon and, after installing Xubuntu from the Alternate CD, everything seems to work fine. The only thing that is actually not working is the audio card. I've recompiled the alsa-drivers, and I actually hear a "pop" when loading, but then I actually can't play anything. Any hints?

---

### Post by renzokuken on 2007-08-22
any idea what audio chipset you have?

```
lspci -v
``` may help

also, which version of alsa-driver did you compile?

---

### Post by drf_av on 2007-08-22
"Intel Corporation 82801H (ICH8 Family) HD Audio Controller"

And I've just recompiled latest alsa-driver, 1.0.14.

---

### Post by drf_av on 2007-09-09
UPDATE: After installing realtek drivers audio works. Also, I suggest everyone using this laptop to upgrade to Gutsy, as it solves many hardware problems.
Thanks everyone!

---

