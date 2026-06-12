---
title: "Fan spins up even though temperature normal"
date: 2009-10-14
forum: Hardware
---

### Post by jovean on 2009-10-14
Yesterday, the fan on my LG R510 started spinning up on boot - and staying on.  I went into the BIOS and turned off the "Fan always on w/ AC power" (and DC, too; I also wondered how that got reset in the first place) and while the fan is no longer on full-blast all the time, it spins up every twenty seconds or so and stays on for about 10-15 seconds - that is, whenever I do something even mildly taxing.  I have lm-sensors installed (for the Xfce Sensors Plugin; I use Xubuntu), which seems to indicate that the fan is getting switched on at about 44C.  This seems like a normal temperature to me, so I'm wondering if there's a way that I can set it to switch on only when it get's closer to 48 or 50 degrees, because the fan is quite loud and annoying.

---

### Post by Giblet5 on 2009-10-14
The temp sensor software available on any OS is only as accurate as the motherboard's integrated temperature probes.

None of them are reliable or accurate and they are subject to even minor changes in air-flow over the PCB; a glob of cat fur can cause an apparent shift of 20C, even though the physical temperature of the core changed very little or not at all.

That said, I would be suspicious of a CHANGE in behavior.

Do you have a removable CPU? Did you? If so, did you clean/reapply a good thermal transfer coefficient grease in a sparing manner to the heatsink/fan?

Ever considered water-cooling? ;)

---

### Post by jovean on 2009-10-14
Thanks for your response, Giblet5.  The computer is a laptop and it's still in warranty, so while I imagine there is probably some way to remove the processor, I have never tried as I don't want to void it.  The problem/annoyance started after an uneventful outing in a padded backpack ... perhaps I should open it up and see if anything got in that can be removed, and might be causing the problem.

---

### Post by jovean on 2009-10-14
Resolved with compressed air (albeit compressed by my diaphragm ... I know, not the best way ... but worked.)

---

