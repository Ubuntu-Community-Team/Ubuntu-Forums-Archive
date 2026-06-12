---
title: "hardware RAID trouble (not fakeraid) on 8.10"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by chinamusic on 2009-02-23
I have a Highpoint RocketRaid 2224 SATA RAID card with four 500gig Barracudas connected.  The drives are configured as a RAID5 array.  When I boot Ubuntu 8.10 (amd-64) from the CD, it sees the drives as individual drives rather than as a RAID array.  If I boot an XP install CD, and feed it the necessary driver, it sees the 1.5TB RAID, not individual disks.  

Anyone have any idea why this is happening?  If it was a bogus RAID card that uses the driver+cpu to do the heavy lifting, I'd understand, but this is a real RAID card.

Regards,

---

### Post by chinamusic on 2009-02-23
F00k.  Hate to follow-up my own post, but it seems I am mistaken about this RAID card.  It really is a fakeraid and needs a special driver.  So much for that.  I guess I'll just use software RAID instead.

Best regards,

---

