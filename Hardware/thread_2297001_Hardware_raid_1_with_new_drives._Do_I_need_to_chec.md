---
title: "Hardware raid 1 with new drives. Do I need to check for errors first?"
date: 2015-09-30
forum: Hardware
---

### Post by katana-9988 on 2015-09-30
Hi guys, I am doing a hardware raid 1 using two new 4TB drives. Just wondering do you guys recommend doing a check for error under Ubuntu before using them in raid 1?

What I mean is, I will load them normally (each drive by its own) and check for errors for both of them. Then I will enable the hardware raid 1 (If wondering it is a motherboard feature),

Please advise me. And thank you.

---

### Post by weatherman2 on 2015-09-30
You don't "need" to check the drives before using them, but I always do - doesn't hurt.  New drives can be bad.  Why not find out first?

I usually run the extended S.M.A.R.T. test on all new drives, at least drives that have some importance.  You can do this with GSmartControl in Ubuntu.  Check the S.M.A.R.T. Attributes as they are now first, to make sure there aren't any existing problems.  You can test both drives at the same time; each test is actually run by the drive firmware itself and doesn't require almost any CPU from the computer it is hooked up to, beyond checking to see if the test is finished.

The extended test takes hours though on a large drive, probably overnight.  I've found that the estimates for actual run time of the extended test to be very optimistic on these big drives.  Don't count on four hours if that's how long it tells you it will take.  Plan on overnight.

Then check the S.M.A.R.T. Attributes again in GSmartControl after the tests have run.

---

### Post by katana-9988 on 2015-10-01
Thanks for the info. One more thing, I am wondering if I can do the check when the drives are in hardware RAID 1 from the motherboard. Will the GSmartControl see it as one drive or two?

---

### Post by tgalati4 on 2015-10-01
The tests need to be performed on each drive separately.  You can run *badblocks* as well.  This is a simple test that will try to read every sector on the drive.  I don't recommend the destructive/write test because you can heat up the drive heads and distort them, making the drive unreliable in the future.

A big drive needs a break-in period before putting it to use.  As the mechanical components age, their performance will vary.  You want to eliminate a bad drive early, but you don't want to wear it out either from too much write testing.  It's a balance.

---

### Post by weatherman2 on 2015-10-01
> **katana-9988 said:**
> Thanks for the info. One more thing, I am wondering if I can do the check when the drives are in hardware RAID 1 from the motherboard. Will the GSmartControl see it as one drive or two?

GSmartControl will see the two drives as individual drives - it does not work at the filesystem level.  It probably isn't even aware that you have a RAID.

---

