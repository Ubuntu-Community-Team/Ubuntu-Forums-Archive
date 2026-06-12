---
title: "Which file system for speed?"
date: 2008-08-29
forum: General Help
---

### Post by Tom--d on 2008-08-29
Hello,

At the moment. My / is in ext3 and I know its the safest one (at corruption) but you sacrifice some speed. (I think).
And I was wondering which file system is good for speed, and why?
Should I just stay with ext3?

My /home is staying in ext3.

Thanks,
Tom :)

---

### Post by justleen on 2008-08-29
ext2 is faster then ext3 and xfs.

i'd stick with ext3 though

---

### Post by mrmorris on 2008-08-29
The killer file system has got to be Reiser4. Pun intended.

---

### Post by mixmaster on 2008-08-29
There is no best.  Even speed comparisons will vary depending on the mix of read and write operations, the block size, the non-disk related CPU load (some FS's are more CPU intensive than others).  Unless you have really specialist requirements ext3 will give the best overall mix of performance and safety.

If you want to play you can convert all your rarely-written filesystems (eg /boot & /opt) to ext2 but I would be willing to bet you won't see any difference.

TBH, for the average user the best way to improve file system performance is to buy a faster hard disk :)

---

### Post by Krupski on 2008-08-29
> **Tom--d said:**
> Hello,

At the moment. My / is in ext3 and I know its the safest one (at corruption) but you sacrifice some speed. (I think).
And I was wondering which file system is good for speed, and why?
Should I just stay with ext3?

My /home is staying in ext3.

Thanks,
Tom :)

I asked the same question a few days back. I discovered that XFS was a LOT faster than EXT3 and red flags went up.

If XFS was (seemingly) so much better, why isn't it the Ubuntu default?

The answer I finally got was that EXT3 is more robust as far as data integrity and crash recovery is concerned.

So, I went back to EXT3.

---

### Post by Tom--d on 2008-08-29
Thank you for clearing this up for me.
I have not decided that I will stick to ext3.

---

