---
title: "Ubuntu hangs"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by GrumpyBob on 2005-12-28
For a few weeks, I have found Ubuntu hanging on me (Breezy on an IBM Thinkpad).  It's never been clearly attributable to a specific app or action on my part.  Finally a couple of days ago, the whole system became unbootable, and fsck failed to sort out the drive (inode errors everywhere).  I've now set up the entire system again (this time with home folders on a separate partition).  I doubt a hardware problem, the WinXP partition seems OK.

However, I am still wondering what was causing the hang-ups - is it likely to have been caused by me hibernating the computer rather than switching off?  There were some messages about suspending to disk in there somewhere.

Robert

---

### Post by Rinzwind on 2005-12-28
Hibernating sucks :* 
And I think a lot of people agree with me that it sucks when it comes to laptops.

So yes, I say it's fair to suggest it's cuz of hibernate.

BUT!!! Linux creates all kinds of log-files. There's even 1 about the bootprocess. If you can get to your disc go visit /var/log (<- from my mind; not an actual check) and look for a bootlog.
99 out of 100 times it'll have an errormessage that helps you to solve your problem

In the meantime: turn hibernate+suspend OFF.

---

### Post by GrumpyBob on 2005-12-28
It's a bit late to recover the log!  If it starts hanging up again, I'll check the log files for sure.

Thanks,
Robert

---

