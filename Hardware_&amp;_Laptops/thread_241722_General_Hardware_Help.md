---
title: "General Hardware Help"
date: 2006-08-22
forum: Hardware &amp; Laptops
---

### Post by ohzopants on 2006-08-22
This should not be posted on ubuntuforums, but I have nowhere else to turn... :(

My laptop has become virtually unusable after a power failure about a month ago.  After the power failure my system became incredibly slow, I then determined that I had bad sectors on my hard drive so I "fixed" them (or at least I tried to), formatted and installed windows.
That didn't do it and now my cpu is running at 100% at all times.  I did some googling and found out that it could be either bad ram or the hard drive so I performed the following tests:

1) Download ubuntu, run as a livecd with the hard drive removed, incredibly slow
2) Ran the memtest on the ubuntu cd for about 10 hours and nothing came up
3) Put the hard drive back in and removed one of the two ram sticks, boot in to windows still 100% CPU (same result with either piece of ram)

So I'm now pretty convinced that it is neither the hard drive or the RAM causing my problems.  What else could it be?  Anyone ever experience anything like this?

Thanks in advance

---

### Post by meng on 2006-08-22
Okay I'm game for idle speculation:
During this power failure, is it possible that your computer was exposed to a surge? Was it on a protected circuit? Could something have been fried?
Note that the LiveCD does run slower than a hard-disk-installed Ubuntu system, so it's hard to say (particularly without knowing your system specs) what that means.

---

### Post by ohzopants on 2006-08-22
Thanks for the reply first of all.

Yes it is possible that there was a power surge though it is unlikely since it is attached to a surge protector (I'm a physics graduate and I worked in the electrical department of a hardware store for 6 years so it is a good one).

The machine itself is nothing fantastic but it's still got a P4-m 1.8GHz with 768 MB of ram.  I had used the livecd functionality before and it was quite a bit faster.

I also forgot to mention that as another possible fix I updated the BIOS, I figured it that was f*cked reflashing might fix it.  Can a CPU be "slightly" fried and just work badly?  I always figured that would be an all or none sort of thing...

---

### Post by garrye on 2006-08-23
Hmmm I'd say the drive is suspect.  Find either a "zero-fill" utility from the drive manufacturer and run that.  Follow instructions and you should be able to do some diagnostic checks to get SOME idea of drive condition.  Better yet would be to find or buy a copy of Steve Gibson's (grc.com) Spinrite 6.  It is more revealing than for former.  Winbloze's task manager is showing 100% CPU usage?  Clean install?  That is to say zero fill the drive, partition, format, and install?  Could be a bug.  Had a machine the other day.  Thought it was fried.  Ended up being a really bad case of pestware that was really well hidden.

---

