---
title: "SATA drive &quot;disconnects&quot;"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by wizardStan on 2007-07-28
Hi,
my layout is simple.  A 15 gig IDE drive acts as my primary linux drive, and then I have a 250 gig SATA drive as "data".  It's an NTFS mount, since it was actually a WinXP drive originally, and I left it as such just in case I needed to swap back.
ANYwho, I just recently noticed that my SATA drive seems to occasionally "disconnect" for lack of a better word.  The mount points are still there, but attempting to access it returns i/o errors.  Attempting to unmount and remount, it tells me that there's an error with the drive, that I need to boot into Windows and run chkdsk /f, and try again.
I found the solution was simply to shut down and restart.  Doing some searching, I found some stuff to indicate that my drive might be powering down after not being accessed for a time, and Ubuntu is failing to power it back up correctly, although I couldn't find any solutions.
Thinking to myself "SATA drives are hot swappable, aren't they?" I did the stupid thing of disconnecting the drive, and plugging it back in.  Drive came to life again; I could actually hear it spinning back up to full speed.  Stood up and attempted to mount the drive again... same error, no dice.  After about 30 seconds, my computer suddenly froze.  I'm assuming this is the point at which Ubuntu noticed there was "new" hardware, and attempted to install it, which failed.  Hard reset, everything comes back.
First thing I did was create a dummy file (called dummy) and made a cron job to touch the file every minute of every hour of every day of ever month.  It's now happily been churning away for over an hour, I just checked, and drive is still online.  I'll give it some more time, but I think this workaround may have "solved" the problem.
My question is, why do I even have to do this?  Is this a known bug?  Am I even interpreting this bug correctly, or is there maybe something else going on that I don't know about?

Thanks a lot, all.

---

### Post by wizardStan on 2007-07-29
So my "hack" seems to have worked.  I woke up this morning, after about 12 hours of no one using the computer, and was still able to access the drive.  I turned off the cron job, walked away for 30 minutes, and lo and behold, the drive had stopped.
If anyone else encounters this problem, this is a stupidly easy way around it.  I still haven't found anything suggesting why Ubuntu isn't able to bring it back up after it's powered down, though.
Cheers.

---

### Post by ianmac on 2007-07-30
Hmmm...  this may be similar to what I've been experiencing.  Though I've only noticed it in the last, say, week.

My configuration is different - I only have one drive, and it is a 60gb SATA (it is an Inspiron 6000).  Every once in a while programs will start crashing (noticed mostly firefox), and then my gnome icons will start disappearing and becoming icons with exes in the middle.

I eventually have to do a hardware powerdown and restart, which fixes the problem.

Sometimes if I'm at the terminal, I get a Journal I/O commit error.

I will try your workaround to see if that fixes it.

Ian

---

