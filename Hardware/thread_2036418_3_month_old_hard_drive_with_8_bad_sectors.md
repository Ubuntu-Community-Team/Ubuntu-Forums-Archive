---
title: "3 month old hard drive with 8 bad sectors"
date: 2012-08-01
forum: Hardware
---

### Post by Lymphocyte on 2012-08-01
so my harddrive that came with my laptop already has 8 bad sectors. Should i be concerned about it? Maybe just shuffle my ps3s hard drive with it?

---

### Post by ahallubuntu on 2012-08-01
I would be very concerned.  What is the actual S.M.A.R.T. report?  Can you try installing smartmontools and post the output of

sudo smartctl -a /dev/sda

where it is assumed that /dev/sda is your laptop's hard drive?

If they are pending sectors, you may be able to clear them by writing zeros to the drive (which will erase everything) then re-installing.  I have seen drives develop "soft errors" that can be cleared this way and not be a problem again.

If they are reallocated sectors, the drive firmware has already marked them bad and replaced them with spares.  That wouldn't sit right with me on such a new hard drive.

Then again, it's still under warranty, right?  Can you get the manufacturer to replace the hard drive?

---

### Post by efflandt on 2012-08-03
If it is a Seagate or Maxtor drive, seagate.com should have SeaTools to check it, or Western Digital has their diagnostics app at wdc.com.  They can do a non-destructive test, or a test that writes and reads data.

A hard drive reserves some space to transparently remap bad sectors to good sectors.  So if you actually start seeing bad sectors, that is a bad sign that can only get worse.  If it is that new, it should be under warranty.

Many years ago I have had relatively new drives that had issues.  One was a month old Maxtor that kept getting an increasing number of bad sectors.  A 2.5 GB WD started having issues when 75% full.  And at some point I had to fsck a 30 GB WD about every boot.  Never had any trouble with the warranty replacements of any of them.  The 30 GB is still running in an old Celeron 300 server in my basement that ran 24/7 without rebooting for 5 years from July 2006 to July 2011, when temporarily shut down for a 14 hr power failure.

---

