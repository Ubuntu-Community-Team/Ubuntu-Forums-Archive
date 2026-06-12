---
title: "Vertical black lines on wake"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by secundar on 2005-06-03
Tickled that my ASUS Z71V will suspend to disk (Hibernate) but not so tickled when I wake it up: The display is botched with black vertical lines. I can still barely read the display enough to restart.

I toyed with the settings a bit in the NVIDIA Settings app but have not yet olved the problem.

Any other Z71V (2371V) users out there? Any other laptop users with the Nvidia Go 6600 card with the same problem?

Nvidia driver version: 1.0-7174

---

### Post by easterndodo on 2005-12-05
I am not totally sure of this, but a friend of mine has an Acer laptop with Nvidia video card, and he cannot use suspension or hibernation with the drivers provided by Nvidia:

So you would have 2 chances:
1) Use the Nvidia driver (so 3d acceleration) and forget about hibernation and standby
2) Use the standard X.Org or Xfree86 driver, suspension and hibernation should work (best if you have a kernel above 2.6.12) and forget about 3d acceleration.

I heard that in some time new versions of Nvidia driver should support hibernation and resuming.

Sorry for the displeasure! :(

---

