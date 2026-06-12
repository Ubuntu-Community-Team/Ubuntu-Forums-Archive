---
title: "hp dv4000 perfect Ubuntu laptop?"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by quietglow on 2005-12-06
I know why you guys didn't come up with a soution to the resolution problem on my gateway: you wanted me to return it and get the PERFECT Ubuntu laptop, right? I just finished an install of Breezy on this DV4000 (which is on sale right now at BestBuy!) and every major area of laptop concern seems to be working out of the box: wireless , screen res, suspend etc. It even doesn't break the network connection when coming back from suspend! I'll be writing up a contribution to the laptop team page after I so some more work with it, but as it stands this is BY FAR the most 'out of the box' Ubuntu laptop I've set up (and this is about the 7th)!

---

### Post by korona100 on 2005-12-06
I just installed Ubuntu on my dv4000 (it also has XP on it) and the wireless was not detected. Also, if I press the wireless button it does not come on. Any ideas?
--Mark

---

### Post by quietglow on 2005-12-06
The light never does come on for me, though the card does work--it was actually even detected in the install. Was yours not?

Do you know what card you have (sometimes they aren't standard)? Mine is using the ipw2200 module. Do an 

```
lsmod
```

and look for ipw2200

---

