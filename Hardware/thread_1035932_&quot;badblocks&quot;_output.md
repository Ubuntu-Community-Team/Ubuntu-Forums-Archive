---
title: "&quot;badblocks&quot; output"
date: 2009-01-10
forum: Hardware
---

### Post by cong06 on 2009-01-10
So i've spent some time looking through man pages, for badblocks and for e2fsck.

I've successfully run badblocks (-s -v -w) for a total of ~50 hours on my external. enough time that if it was cumulative it would have worked. (not understanding how the tool worked compelled me to kill it half way through to restart after getting security updates)

I was wondering if someone could point out to me if the checker prints out bad blocks as it goes or if it dumps them all at the end. I didn't get any badblock print out yets (only status reports) so I'd feel better about cutting corners (I just want to use my hard drive again) if it prints out the bad blocks as it goes.

I did manage to get to the 3rd run in the write test (0xaa, 0x55, 0xff)

I'm about to start a e2fsck run, because I just learned last night that badblocks doesn't fix the problems, only list them.

---

