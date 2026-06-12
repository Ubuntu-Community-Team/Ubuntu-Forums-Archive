---
title: "Vanishing hard drives"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by Dekafox on 2008-04-14
I found my OS HD was on its deathbed last night, so I swapped in a spare one and decided to give Ubuntu a try, and ran into an odd issue.

I'm running a Gigabyte K8-NSNXP on this machine, with my two optical drives on the regular IDE, and 4 HDs on the "RAID" IDE spots.  When I use an old x64 6.06 LTS CD I got last year or the year before, it sees all the drives fine, as /dev/hde1 through /dev/hdh1, I believe.  When I try using a x64 7.10 CD, it only detects the two Master drives, and lists them as /dev/hda and /dev/hdb.  All 4 drives have the jumpers set to Cable Select.  I haven't gotten a chance yet to try x64 Hardy and see if it sees them all or not.  Any idea what might be going on here, and if it's fixed in Hardy?

I haven't tried mounting them, since they're NTFS(except /dev/hde1 which is the future OS disk) and I wasn't sure if the LiveCD portion included ntfs-3g.

*edit* I tried the beta 8.04 CD, and it saw all the drives, so whatever it was is specific to 7.10 apparently.

---

