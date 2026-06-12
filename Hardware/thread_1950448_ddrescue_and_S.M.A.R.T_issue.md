---
title: "ddrescue and S.M.A.R.T issue"
date: 2012-03-31
forum: Hardware
---

### Post by Packrat1947 on 2012-03-31
I've just had an unusual issue.   I had a customer's machine here and used ddrescue to clone the drive to a nearly new 500 gig drive.  Windows would not recognize the drive because of the errors.

The imaging went fine except that now the new drive reports that SMART has been tipped.  CrystalDiskInfo reports: "reallocated sector counts"  I've wiped the drive, but can not find a way to reset SMART.  I realize that it is a firmware issue. 

I could probably throw it into an external case and not be bothered any more.   Has anyone else had bad SMART records moved to a different drive?

Packrat1947

---

### Post by ahallubuntu on 2012-03-31
S.M.A.R.T. records can't "move to a different drive" when it is cloned.  Reallocated sectors means that the drive you are looking at had some failed sectors and the drive's firmware marked them as bad and replaced them with spares.  This is a sign that the drive is gradually failing though it could be a very long time til that happens.  You are technically OK until that drive runs out of spare sectors - though using spare sectors can reduce performance, since the spares may be located nowhere near the original failed sectors they have replaced.

Even a new drive could fail quickly.  Just being new doesn't guarantee a drive won't have bad sectors the next day.  (Meanwhile, some drives will run for years and never throw a bad sector.)  You can't get rid of reallocated sectors just by zeroing the drive.

---

### Post by Packrat1947 on 2012-04-01
Thanks for the reply.  The coincidence is what has me wondering.

BTW, Seatools reports "DST - failed"  But then the long and short tests pass OK.

Packrat1947

---

### Post by ahallubuntu on 2012-04-01
Yeah, I'd expect the S.M.A.R.T. tests to pass, because technically your drive is "healthy" as all sectors can be read/written. Having a few reallocated sectors is not unusual for an older drive and you can certainly still use such a drive.  But knowing a few sectors have failed means a few more will probably fail sooner or later, and eventually the drive will run out of spares.  

It would be more worrisome on an "almost new" drive.

I wouldn't personally use such a drive for anything important.  I do use similar drives for projects like media centers where the OS drive can completely fail and I wouldn't care as I have no important data to worry about.

If this drive is still under warranty, I'd probably RMA it and get a replacement myself.

---

