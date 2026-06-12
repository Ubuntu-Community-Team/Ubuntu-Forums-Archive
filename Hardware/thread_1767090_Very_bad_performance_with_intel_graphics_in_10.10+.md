---
title: "Very bad performance with intel graphics in 10.10+"
date: 2011-05-25
forum: Hardware
---

### Post by Zzzdark on 2011-05-25
Hi,
After recently having XP fail on me for the third time in as many weeks, I looked into other alternatives, and decided to put Ubuntu (which I have SOME experience with) onto my netbook. 
I initially went with 11.04, but graphics performance was incredibly bad. Desktop effects barely worked, tux racer wouldn't run, and several old games which worked perfectly under windows were extremely laggy under wine. The netbook is now running 10.04 LTS which runs without a single problem with graphics (but not quite as well as XP), but I'd much rather have 11.04. 
My investigations have revealed that 10.10+ uses the 
"intel" driver for my 915GM/GMS/910GML, where as 10.04 uses "i915". My question is, is there any way of using the "i915" driver in 11.04, or fixing whatever issue it is that makes the "intel" driver work so badly, or anything really?

---

### Post by prshah on 2011-05-25
> **Zzzdark said:**
> 
My investigations have revealed that 10.10+ uses the 
"intel" driver for my 915GM/GMS/910GML, where as 10.04 uses "i915". My question is, is there any way of using the "i915" driver in 11.04, or fixing whatever issue it is that makes the "intel" driver work so badly, or anything really?

"intel" and "i915" are one and the same. There is no difference in the packages, just the name. There are a number of old tweaks for pre 10.04 packages; a search of the forums for "MigrationHeuristic" should turn up a list.

However, please post back if you want more details, or have difficulties in following the other posts.

I would suggest that you stick with Ubuntu 11.04 and either classic or Unity2D. The performance is acceptable.

---

