---
title: "Did I screw up bad?"
date: 2008-11-13
forum: Hardware
---

### Post by jeremywitt on 2008-11-13
Did I mess up BIG time? I have two partitions set up... one with Hardy and the other with XP. I ran out of space on the XP partition and decided very sporadically without thinking to just resize the partition via booting from live CD --> Partition program. I freed some space from the end of the Hardy partition and added it to the beginning of the XP partition.
When I shutdown the live CD for reboot it ran something across the screen with a whole bunch of numbers and some text after but all i can remember is something about a sector... but the numbers on the left kept getting bigger and bigger. It didn't stop so i just turned the power off.
When I reset it, I first checked to make sure Ubuntu was ok... it was! WHEW!! So I reset and attempted loading windows but with no luck... it got stuck on the blue screen with the windows logo in the center.
I reloaded Ubuntu and attempted to mount the windows partition but it won't work... any ideas to recover the files on the windows partition???

---

### Post by jpkotta on 2008-11-15
You can't increase partitions from the beginning.  You can only add space at the end.  Same goes for shinking.  If you saved your partition table, you can just rewrite it.  If you made a back up (like all the partitioning tools tell you to), you can restore the data.  Otherwise, you're SOL.  

In theory, you can rewrite the partition table with the same offsets as before, and partitions will work as before.  IOW, the data should still be there, but the computer just doesn't know it.  If you *really* want your data back, you could just try different offsets until you get the one you had before.  Maybe there is a magic program that does this somewhat automatically.

---

