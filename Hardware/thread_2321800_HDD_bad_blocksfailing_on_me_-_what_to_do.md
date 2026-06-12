---
title: "HDD bad blocks/failing on me - what to do?"
date: 2016-04-24
forum: Hardware
---

### Post by lakeshore2985 on 2016-04-24
From the "Disks" program in Ubuntu I can see one of my old HDDs is dying (8/16 bad sectors), and when I try to run any self-test the application says "SELF-TEST FAILED".

So I went on dig a little bit more and found a couple of interesting commands:

```
dd if=/dev/zero of=/dev/sdx
```

After doing the "low-level format", drive still has bad sectors (it says 'UNC' for 'uncorrectable errors').

Now my question is, what do the following commands actually do? Take a look below:

```
sudo badblocks /dev/sdx
```

```
sudo fsck.ext4 -cc /dev/sdx
```

This is very annoying, been experiencing random failures and corrupted files from time to time.

Will somebody guide me on how to not let the OS write to those bad sectors again?

---

### Post by weatherman2 on 2016-04-24
Badblocks should be unnecessary with modern hard drives.  For a long time now, hard drives have had built-in "spare" sectors, and when a sector fails, the sector is automatically marked "do not use" by the drive's firmware, and it is re-allocated to one of the spare sectors.  (And then the number of reallocated sectors in S.M.A.R.T. is increased by one sector.)  The OS is not even aware of this and doesn't need to be - that's the point, to eliminate the need for something like badblocks.

There are cases where sectors fail but can't be reallocated by the drive firmware - usually you see them as "pending" sectors.  (There was an attempt to read them but the firmware is still waiting to hear from them, before they can be re-allocated.)  Sometimes this means the drive's surface is failing - in which case, using something like bad blocks is pointless, because the drive is dying and more and more sectors will fail, so why bother?  Sometimes pending sectors seem to be "soft" errors that can be completely cleared by zeroing the drive (like you did).  I have done that a number of times; sometimes the drive works reliably thereafter, sometimes not.  The important S.M.A.R.T. indicator for me is the RAW value of "Current Pending Sectors."  Other "bad sectors" may be ignorable; "reallocated" sectors as I said above are not fatal until too many fail and the drive runs out of spares.

If you zeroed the drive, all pending sectors cleared, and it now passes the Extended S.M.A.R.T. test, I'd probably just use it.  Then again, I always assume any drive could fail and make backups of absolutely everything, anyway.  I would keep an extra eye on this suspect drive.  I've had a few drives go many years without any glitch and others that start failing again at some point (maybe at different sectors than the first time - so "badblocks" would have been a waste of time, anyway, right?).

---

### Post by lakeshore2985 on 2016-04-25
> There are cases where sectors fail but can't be reallocated by the drive  firmware - usually you see them as "pending" sectors.  (There was an  attempt to read them but the firmware is still waiting to hear from  them, before they can be re-allocated.)  Sometimes this means the  drive's surface is failing - in which case, using something like bad  blocks is pointless, because the drive is dying and more and more  sectors will fail

Well, in my case though I don't see no pending sectors or anything related. It is really bad sectors and I keep getting I/O errors everywhere.

Last time I zeroed the drive I got another I/O message again, but only after some good 2~3 hours when the process was done. Not sure what actually happened there.

I have a question regarding some of the commands, like what they do and such. For example, what is the difference between the parameters "-c" and "-cc" for "fsck" ? From the man page I read something about destructive and non-destructive read-write test, but I have no clue what that means.

Plus, if you would be so kind to explain, what do you mean by the firmware of the drive(s) reallocating bad sectors automatically? I mean I thought this was done by the OS instead, not the drive? It's been more than 24 hours since I started another "fsck.ext4 -cc" instance hoping that will at least minimize some of the major problems I've been having with file corruption with this defective rather big drive.

---

