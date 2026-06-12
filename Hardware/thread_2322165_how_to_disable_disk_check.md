---
title: "how to disable disk check?"
date: 2016-04-26
forum: Hardware
---

### Post by pickarooney on 2016-04-26
Every time I boot up I'm subjected to a laborious check on my two hard drives. This has been going on for about six months.
I have changed both hard drives since, but the problem persists. There is no apparent hardware issue.
As of 16.10 it has become impossible to cancel the check. It takes about 10 minutes to complete.

I've used tune2fs to set the checks to every 60 boots on each drive partition, but they are checked each time nevertheless.

During the boot sequence there message 'Started File system check daemon' appears followed by the checks. I can't find any information online on this daemon or how to disable it.

---

### Post by weatherman2 on 2016-04-26
Are you sure there isn't some real corruption in the file systems that is triggering the checks?  You're sure these hard drives are healthy?  (Is this something new you have started to experience only in the last few releases?)

I don't have this problem on any of my Ubuntu systems, although I am not using anything newer than 14.04.  I have always used tune2fs in the past to disable checks completely (not necessarily a safe thing to do - filesystems should be checked occasionally.)

---

### Post by sammiev on 2016-04-26
Mine does a disk check on boot but only takes about 2 seconds. ( 16.04 )

Then again I'm using 16.04 as 16.10 ( YakketyYak ) is under development and only started a few days a go.

I do have a partition for 16.10 but only had a few updates so far. Boots in about the same amount of time.

---

### Post by ajgreeny on 2016-04-26
@ sammiev.
I have 16.04 as a VM in VBox and I always see a message that the filesystem is clean, but it passes by that so quickly and s still a fast boot so I don't believe that it actually does a full fsck, which would take much longer.

Is that what you also see?

---

### Post by sammiev on 2016-04-26
> **ajgreeny said:**
> @ sammiev.
I have 16.04 as a VM in VBox and I always see a message that the filesystem is clean, but it passes by that so quickly and s still a fast boot so I don't believe that it actually does a full fsck, which would take much longer.

Is that what you also see?

Correct.

My full boot times are still under 5 seconds.

---

### Post by QLee on 2016-04-27
It is my understanding that at boot time the system checks to see if the filesystem was marked as "cleanly unmounted" (I don't know if that is the exact term), if not then it does a fscheck. So most of the time it goes by quickly and we only notice it when the system has to do a complete file check.

The OP is running 16.10 so I wouldn't be surprised if everything isn't working correctly yet. There is a Debian bug about systemd running fscheck on every boot but I do not know if this is related.

One thing the poster might try is to change the sixth field of line for the two filesystems in the fstab to 0 (zero) and see if it honors that, which should mean never file check (not recommended).

Shouldn't this thread be moved to discussions of the Development Version?

---

### Post by vasa1 on 2016-04-27
> **QLee said:**
> ...
The OP is running 16.10 ...

Shouldn't this thread be moved to discussions of the Development Version?

I'm betting that that's a typing error ;)

Let's wait for OP to reappear!

---

### Post by QLee on 2016-04-27
> **vasa1 said:**
> I'm betting that that's a typing error ;)

Let's wait for OP to reappear!

I agree. Naturally, we can only work with the data we have.

If the OP isn't a beta tester, might not even understand what I wrote.

---

### Post by ajgreeny on 2016-04-27
> **vasa1 said:**
> I'm betting that that's a typing error ;)

Let's wait for OP to reappear!
Yes, I assumed that as well.  Somebody who can not figure out this sort of filecheck problem would probably never find 16.10 as it is not available to all and sundry without a search for the development version.

We wait and see.

---

