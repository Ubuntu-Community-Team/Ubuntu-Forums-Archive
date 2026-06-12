---
title: "ddrescue freezes system while copying"
date: 2008-11-23
forum: General Help
---

### Post by skullmunky on 2008-11-23
What do you do if even ddrescue freezes while trying to rescue a drive?

I think I do have a dying drive.  The symptoms are:

- occasional hard system freezes when doing innocuous things, like file browsing
- the SMART status shows I have some Current_Pending_Sector blocks (6, to be exact)
- SMART selftest fails with read errors
- badblocks and fsck cause a hard freeze

I've been using the "Zero the bad block" technique from the smartmontools site, and was able to get Current_Pending_Sector down to 0 and successfully fsck the drive.  I thought that was good, but then two days later the symptoms reappeared.  So I figure better safe than sorry, so I used ddrescue try and just get a clone and then repair that.  

But, it froze up completely less than a quarter of the way through (it's a 500GB drive).  Even the SysRQ keys wouldn't work.  

This worried me because I thought ddrescue was supposed to be able to recover from read errors on damaged drives gracefully.

I'm trying to decide whether to repeat the bad-block wiping process to try and get the pending sector count back down, or if that's futile and instead I should use incremental ddrescue copies to work around the bad blocks.  

Thankful for any advice ...


edit: well, I repeated more bad-block reallocation, kept going until the drive passed the SMART long test, and then ddrescue succeeded.  I'll go carve the old drive into the shape of a turkey.

---

