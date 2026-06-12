---
title: "Disk Failure is Imminent?"
date: 2011-07-09
forum: Hardware
---

### Post by PartisanEntity on 2011-07-09
Hi all,

Since a couple days now, Ubuntu is informing me that my external USB HDD is reporting errors.

The HDD is about 1.5 years old, a LaCie 1TB HDD.

The reported errors are:

[B]Reallocated Sector Count
Assessment: Failing
Values:
Normalized:1
Worst: 1
Threshold: 5
Value: 741 Sectors[/B]

and
[B]
Current Pending Sector Count
Assessment: Warning
Values:
Normalized: 43
Worst: 43
Threshold: 0
Value 309 Sectors[/B]

I have backed up the drive, but I am interested to know, how serious are these errors, or is this perhaps a bug in Ubuntu?

Is this drive going to die any day now?

Anything I can do to save the drive?

Thanks!

---

### Post by PartisanEntity on 2011-07-09
Here is a screenshot of the two errors.

Is it normal for a drive to show such errors after only 1.5 years?

---

### Post by DanneStrat on 2011-07-10
> I have backed up the drive, but I am interested to know, how serious are these errors, or is this perhaps a bug in Ubuntu?

The info reported in the "disk utility" is read from the harddrive's built in s.m.a.r.t. sensor and should be taken seriously. A failing drive may last a long time after it's been deemed as "failing" but once the drive has started to develop "bad sectors" it will fail eventually. 

Now, your drive shows a substantial amount of reallocated sectors. A reallocated sector is when read/write errors is discovered in a sector and the sector is marked as "reallocated" and the data is moved to a spare area of the drive. These reallocated sectors are also referred to as "bad sectors". It's good that you made a backup of the drive. You can continue to use the drive but you have to be aware that it may fail eventually.

I have to tell you this. A while ago i got a laptop from a friend. The laptop was in good cosmetic condition but once, it had a fall from a couch. When I got it, I was not aware of this so I installed ubuntu on the drive. When everything was properly configured, somehow I got into disk-utility and to my surprise, the drive had 35000+ reallocated sectors! I decided that the drive had to go so I bought a new one.

> Is it normal for a drive to show such errors after only 1.5 years?

It depends. A while ago google made a test to see how long drives would last and some failed after a very short time.
See here: [labs.google.com/papers/disk_failures.pdf]("labs.google.com/papers/disk_failures.pdf")

> Anything I can do to save the drive?

In short, no.
At some point, I've read some forum posts from people with "bad" smart-values and some common advice suggested is to do a complete "zeroing" of the drive(you can do this with killdisk or dd etc.). While this will "unmark" bad sectors discovered by the operating system on software-level(soft bad sectors) it can do nothing for the bad sectors found by smart
(hard bad sectors found on hardware-level).

I hope this answers your questions. If you still have questions let me know.

You can read more about s.m.a.r.t. data here:

[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

---

### Post by psusi on 2011-07-10
If it is still under warranty, contact the manufacturer and get it replaced.

---

