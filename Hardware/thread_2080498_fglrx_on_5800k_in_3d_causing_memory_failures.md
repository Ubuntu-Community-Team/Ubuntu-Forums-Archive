---
title: "fglrx on 5800k in 3d causing memory failures"
date: 2012-11-04
forum: Hardware
---

### Post by lordzanny on 2012-11-04
I have a fresh media center pc build with an a10-5800k and some corsair 2133 ram.  At the XMP profile, with stock speed, memtest86 and memtest86+ have passed runs for 6 hours and ~10 runs each.  The radeon driver works fine.  Fglrx runs fine (sans the need to install generic linux headers) up until I use any 3d application.   And soon after starting to run such an application I get systemic memory failures that leave the system unresponsive and the display in a corrupt state with malformed patches of green and blue pixels that stutter.

If I downclock the memory to 1866, this never happens.  If I use the open source driver, it doesn't happen.  Usage outside of gpu intensive functions don't cause this effect.  It might be a DMI issue on the mobo, it might be the memory, or it might be bad gpu components on the die, I can't tell.  Any insights ye of the coffee drugged Aztec god?  I'd try sticking the memory in my p6t nehalem build, but the board doesn't support that speed and I'd have to attribute issues there to that anyway.

---

