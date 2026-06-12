---
title: "bitcoind getting block checksum mismatch"
date: 2017-01-09
forum: Hardware
---

### Post by lordbah2 on 2017-01-09
This computer which has run bitcoind for 4 years or so has for the past week seen it die with

```
2017-01-07 02:45:45 Corruption: block checksum mismatch
2017-01-07 02:45:45 *** System error while flushing: Database corrupted
2017-01-07 02:45:45 Error: Error: A fatal internal error occurred, see debug.log for details

```
Not always on the same block. Sometimes while re-fetching blocks from a couple years ago, sometimes on more recent ones.

No other program reports any errors (that I've noticed).

fsck finds no errors with the disk.

I installed from scratch on a separate hard disk - and had the same result.

I ran memtest86 and it found no errors with memory.

Is there a more stressful memory tester, as in using multiple CPUs simultaneously?

---

### Post by lordbah2 on 2017-02-08
I dropped from 24GB RAM to 16GB and ran for a week. No problem. So it must be the memory I pulled was bad, right? Put that RAM back in place of another bank, so still running with 16GB - no problem. Soooo .... intermittent issue with those sockets, or the motherboard? I don't know.

---

