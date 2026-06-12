---
title: "USB not detecting in Ubuntu 10.04"
date: 2010-11-09
forum: Hardware
---

### Post by KrishnaMohan.A.M on 2010-11-09
A few months back my SMPS crashed and blows up my onboard sound. I replaced the SMPS and bought a new sound card(USB was working well then). Now my USB drives are not detecting. My primary inference is the defect in the motherboard caused by the SMPS failure. How can I fix it...?
My PC Configuration

[LIST]
[*]Intel 945 Chipset
[*]Intel Core 2 Duo
[*]Ubuntu 10.04/Window 7
[*]1 GB DDR2 Ram
[/LIST]

---

### Post by frankbooth on 2010-11-09
Misunderstood the post, never mind.

---

### Post by prshah on 2010-11-09
> **KrishnaMohan.A.M said:**
> A few months back my SMPS crashed and blows up my onboard sound. I replaced the SMPS and bought a new sound card(USB was working well then).

A low-level electrical fault (such as lightning strike, SMPS blowout) will likely affect multiple systems, such as (onboard) sound, video, LAN and USB. This is one of the drawbacks of fully integrated boards. It is very likely that USB was compromised, but problems didn't show up till later.

The good news is that if the board is under warranty (most boards carry a 3-year warranty) you can get a replacement, or if there is no warranty or warranty is refused, you can probably attempt a repair: the problem will be confined to bad capacitors, since solid-state electronics are not so easily affected.

Bad caps are easy to replace if one has rudimentary desolder/soldering skills, or you can find a electronics repairman to do it for you. Replace capacitors with the same voltage and same or slightly higher farads rating and temp rating. Capacitors will be easily available at your local electronics market, and chances are that you will find a person to do the replacement there as well.

How can you check it's bad caps? Look at the capacitors on the board for "bulging" tops, or leaking gunk (electrolytes).

If all else fails, you will have to change your motherboard; there is nothing software can do in this case.

---

