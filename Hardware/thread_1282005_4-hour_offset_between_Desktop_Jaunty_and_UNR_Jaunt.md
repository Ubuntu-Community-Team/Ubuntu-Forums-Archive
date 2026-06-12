---
title: "4-hour offset between Desktop Jaunty and UNR Jaunty"
date: 2009-10-03
forum: Hardware
---

### Post by apax on 2009-10-03
Here's a weird problem:

I have an old laptop (Thinkpad R50) that I use as my home PC, and a netbook (MSI Wind U123), dual-booted, that I want to use for occasional work while traveling.  I installed Jaunty 9.04 on both (Desktop and UNR, respectively).  I want to exchange files using a USB flash drive formatted under Windows (I need to be able to also access it at work).  However there is a 4-hour difference between the two machines, which prevents rsync from properly synchronizing changes.

This is an example of ls -l on one file, created on the R50, as seen on the R50:

-rwx------ 1 ap root  83481 2009-09-19 16:03 outline1.pdf

and this is the same file as seen when the USB stick is plugged into the U123:

-rwx------ 1 ap root  83481 2009-09-19 20:03 outline1.pdf

Each machine sees correctly its own time, but not the other's.  I tried the reverse -- creating a file on the U123.  The time stamp appears correct on the U123.  Move the USB stick to the R50, and it's 4 hours earlier.  Either there is a time warp in the middle of my desk, or the two machines are encoding time stamps differently (at least when writing to a DOS filesystem).

As a last test, I plugged the same USB stick into a Windows machine, and it agrees with the U123, not with the R50.  If there's a bug, it's in the Desktop edition of 9.04 (at least as applied to the R50), not in UNR.

Both machines are running on the same time and time zone (Eastern Daylight Time).

Any ideas?

Thanks!

---

