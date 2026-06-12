---
title: "Patching: Focus on context; ignore line numbers"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by goldfish2 on 2009-05-13
I want to patch version 13 of a program, but the patch is designed for version 12.  The line numbers in the patch file are way off now, but the context should be good for the most part.

Is there anyway for it to ignore the line numbers and only use context clues?  Or use the line numbers of the closest matching context?

I tried using -fuzz, but that is the opposite of what I want where it ignores context.  When I used this it simply added the new lines but in the complete wrong spot.

Thanks,
~GoldFish

---

