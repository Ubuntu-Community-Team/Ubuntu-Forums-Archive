---
title: "Corrupted initrd on Jaunty live USB"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by grey.rabbit on 2009-05-31
The initrd.gz on my liveUSB got corrupted, so I couldn't boot - the error message was "Aborted because of bad gzip magic numbers", followed by a kernel panic.

So I copied the initrd of the regular liveCD over to the liveUSB, and now I can boot again, but persistency is not working.

Two questions:
1. Is persistency not working because I use the initrd of the live CD?
2. If yes, how can I fix that (i.e. how can I generate the initrd of the liveUSB system)?

---

