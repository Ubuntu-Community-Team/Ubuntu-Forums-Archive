---
title: "Karmic doesn't boot consistently on Toshiba Satellite"
date: 2009-11-07
forum: Hardware
---

### Post by FunkeyMonk on 2009-11-07
I'm having problems booting my Toshiba Satellite M115 with Karmic Koala
9.10 boots OK with kernel 2.6.28, but has no trackpad support.

If I try to boot 9.10 with 2.6.31, it fails about 85-90% of the time.   Usually it's stuck with the code:
```
ata4: lost interrupt (Status 0x50)
```

The other 10-15% of the time it boots just fine, but the wireless networking fails.   When it DOES boot, it takes SEVERAL minutes.

The 2.6.28 kernel boots much faster.

When I upgraded to Ibex, I had initial problems booting this machine -- had to comment out a few lines of code, addressed here: [http://ubuntuforums.org/showthread.php?t=989321](http://ubuntuforums.org/showthread.php?t=989321)

But this seems a very different issue.   I should add that the system boots wonderfully from my liveCD flash drive.

Any ideas?

---

