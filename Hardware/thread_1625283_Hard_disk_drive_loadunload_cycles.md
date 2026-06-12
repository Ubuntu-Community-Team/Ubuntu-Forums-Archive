---
title: "Hard disk drive load/unload cycles"
date: 2010-11-18
forum: Hardware
---

### Post by bwbloch on 2010-11-18
I have an Asus UL30a and came across the [wiki page]("https://wiki.ubuntu.com/AsusUL/HddCycles") which advised of a possible issue with too-rapid HDD load/unload cycles.  I checked this on my machine; it was in fact a problem.  I implemented the "direct" fix and it worked.  My question is: Can you slow these cycles down *too* much?  Before the fix, I had a cycle count increase of 7 in four minutes; after the fix, there was no increase at all in four minutes.  After rebooting, it *seemed* that my machine was responding more slowly, but perhaps that's just my imagination. Can slowing down the cycles affect performance? Is there an optimal cycle count increase rate that one should aim for?

Thanks!

---

### Post by dcstar on 2010-11-19
> **bwbloch said:**
> I have an Asus UL30a and came across the [wiki page]("https://wiki.ubuntu.com/AsusUL/HddCycles") which advised of a possible issue with too-rapid HDD load/unload cycles.  I checked this on my machine; it was in fact a problem.  I implemented the "direct" fix and it worked.  My question is: Can you slow these cycles down *too* much?  Before the fix, I had a cycle count increase of 7 in four minutes; after the fix, there was no increase at all in four minutes.  After rebooting, it *seemed* that my machine was responding more slowly, but perhaps that's just my imagination. Can slowing down the cycles affect performance? Is there an optimal cycle count increase rate that one should aim for?

Thanks!

It will only increase **power consumption** as the disk is not turned off as frequently - if anything it will increase performance because there is no wait for the disk to reload.

---

