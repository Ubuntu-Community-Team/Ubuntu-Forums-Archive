---
title: "RAID advice needed"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by moonlightcheese on 2008-02-05
i'm setting up a raid5 (soft raid) with 4x320 7200.10's and i'm curious which raid card i should get... looking for affordability here.

and on a side note, whats the point in a raid card with 1xSATA port?

---

### Post by KyleAnderson on 2008-02-05
You mentioned soft raid, and you are looking for affordability = software raid?

You shouldn't get a raid card if that is the case, as long as your motherboard has the necissary plugs. If you don't have enough plugs, you can get a cheap addon card (not raid) and still do the raid in software.

There will be a performance hit if you are doing raid5 in software, but if you are looking for cheap, that is the way to go.

Raid card with only one sata port? Sounds silly. The R in raid means redundant! :)

---

### Post by astrotech226 on 2008-02-05
The only thing you gain by having a raid card is the fact that there is a piece of dedicated hardware to process the raid information (parity, etc).  They are faster than software raids.

In my experience, I only use raid hardware for really fast scsi drives or large arrays of many drives.  All of my sata installs use software raid 5s.  I just installed Ubuntu Server 7.10 for two machines that each had three 750G sata drives and I set the software raid up during the initial install.

Let me know if you need help with it and I'll type up a quick how-to.

---

### Post by moonlightcheese on 2008-02-05
my software raid5 crapped out on me because i'm a total noob and didn't --zero-superblock the drives i was building the raid on.  they originally carried a 3 disk raid 5 that i killed and built a 4 disk raid 5.  i added the 4th drive later and it rebuilt beautifully.  then it died.  i don't really trust software raid anymore as i lost 520GB of data and that's just not something i want to screw around with again.  i need a serious raid solution and i realize i'm going to have to shell money out this time.  losing 520GB is just unacceptable and soft raid won't cut it.

---

