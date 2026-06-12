---
title: "Dell M90 Fans"
date: 2009-05-24
forum: Hardware
---

### Post by Albatrosses on 2009-05-24
I'm having a problem with Ubuntu (64-bit) on my Dell M90 getting fans to work properly.

Since there doesn't seem to be any out-of-the-box-support (i.e. my computer just overheated), I've installed (or rather downloaded and ran) dellfand.  The little utility works great at turning the fans on.  Unfortunately, it seems after my CPU gets over 40-50C some other fan management daemon kicks in and spins all the fans down to 'low', which (obviously) causes the computer to overheat even faster.  Whatever does this and dellfand then get into a fight, and my fans go fast -> slow -> fast -> slow -> fast -> slow every couple seconds.  It's... really annoying.  And then my computer overheats.

I've tried adding (and removing) the 'fan' kernel module, looking for active processes and daemons named 'fan' or 'i8k' with no avail.  What else is doing this!?


Thanks!

---

