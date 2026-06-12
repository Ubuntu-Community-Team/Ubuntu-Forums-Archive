---
title: "Nvidia sli=on in xorg.conf results in other monitors going BLACK?"
date: 2016-08-25
forum: Hardware
---

### Post by nechen on 2016-08-25
Greetings!

I recently got SLI working using nvidia-xconfig --sli=on and after rebooting checked the Nvidia X Server Settings utility and sure enough it said Screen 0 (SLI) on the primary GTX 760.

However, the other 2 monitors I have plugged in are just set to "OFF" under the utility. I tried turning them back on and setting the resolution and refresh rate back and clicking apply / save to xorg.conf but then it would just revert back to off.

Ultimately I had to set --sli=off and do a reboot just to get my monitors back. A thorough search all over the place has yielded nothing except one response I saw that said "Try switching ports on the graphics cards" but to my knowledge in SLI, any additional monitors have to be hooked up to the primary GPU0 when in SLI for it to work at all.

Would anyone mind shedding some light on this? I actually launched Counter-Strike and used nvidia-smi --loop=1 and sure enough both cards were working in unison so I'd like to get this working properly if at all possible.

Thanks!

---

### Post by nechen on 2016-08-25
Bump.

Spent all day trying to find out what's causing this to no avail.

---

