---
title: "Trouble with external HD, data recovery, and ext3"
date: 2009-06-21
forum: Hardware
---

### Post by jxn on 2009-06-21
Hello!

I'm posting as a desperate last-hope for help with recovering data from my usb hard disk.  I have an external 1 TB USB Sata drive, which has been working properly for about 4 or 5 months, but the other day, without warning, the disk would not mount--claiming "bad nfs" (I'm not using nfs), "drive is not mountable", and a host of other errors.

I tried running no-destructive data recovery methods to no avail... eventually, I decided to run testdisk (did not seem to help), and then attempted using gparted's filesystem scan/repair mode... (which, I guess, runs e2fsck with the -y and -f flags).  Anyway, this cycle has been running now for a week and two days straight.  I am hesitant to stop its work, because when I hit cancel it warns of "SEVERE data loss" that seems likely to accompany stopping the app, but I'm starting to wonder if it is doing anything at all or is just in some infinite loop.

Is there some kind of a system log set up in ubuntu so that I can check that it is progressing somehow? (couldn't find anything useful in /var/log, where gentoo would have put those things)  Is there no hope for my precious data?

Also, does ext3 cause excessive wear on external USB drives?  This is the 5th external drive I have burned through in 4 years using ext3.  I don't mistreat them.  They stay in a room-temperature area, in the same spot, free from jostling or magnetic fields.  Two have been Maxtors, one western digital, one simpletech, and now this Seagate FreeAgent, and their lifespans have been consistently pathetic.  I always use mkfs.ext3 with no funky options when setting up the drives.

Thanks!

---

### Post by quixote on 2009-06-22
I'm going to offer mainly sympathy, since I don't know the answer to your questions for sure.

a) 9 days of disk scanning / repairing seems way too long, even for 1TB.  What are you actually hitting when you say "cancel"?  Ctrl-C?  That's what I would try.  

b) When you say you tried testdisk, do you mean you ran it but couldn't see how to use it, or that you ran it and knew how to use it?  There are pretty good instructions [here]("http://www.howtoforge.com/data_recovery_with_testdisk"), for instance, on recovering lost partitions, in case it was the first situation.

c) I don't know where ubuntu puts the log.  I'm sure it's there somewhere . . . sort of like aliens from outer space!  I don't know why they make these things so hard to find!

d) I haven't heard of ext3 being bad for USB hard drives, but that sure is a non-random-looking pattern of failures.  Very odd.

Anyway, hope any of this helps.

---

