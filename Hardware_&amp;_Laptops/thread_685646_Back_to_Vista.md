---
title: "Back to Vista"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by jd937 on 2008-02-02
Ok, so unfortuantely I need to go back to Vista.  I have an acer extensa 5420 with 2 gb ram, 170 gb hard drive and amd x2 processor.  I made the restore disks before installing Ubuntu, only to discover that they don't contain the OS.  when I try to use them it says no partition found, so I'm guessing that the OS is only on the recovery partition, which I reformatted for Ubuntu.  How can I recover this?  Being that it's only been written over once, I can't imagine that a good data recovery program couldn't unearth the partitions, but I can't find anything that is Ubuntu compat.  Or should that even matter as some of them are ISO's that are live CD's?  Or is it possible that I just need to reformat into an NTSF and the then try the restore CD?  Perhaps it just isn't seeing the partition as it's not NTSF?

---

### Post by rogblake on 2008-02-02
Sorry you have to go back to Vista, from what I've seen it's a real train wreck.

None of the recent Acer systems I've seen have had a recovery partition, typically the drive is set up by the factory with two partitions, one for the operating system and the other for making backup images.  The user is supposed to make a set of recovery discs during initial setup, which you have apparently done.

It's pretty likely that the restore software expects to see either a blank hard drive or one formatted with NTFS, it may be getting confused by the "foreign" Linux partition(s). If this is the case, deleting the Linux partitions may be enough to fix the problem.

---

### Post by LaRoza on 2008-02-02
[color="red"]Acting as moderator:[/color]

[http://ubuntuforums.org/showthread.php?t=685641](http://ubuntuforums.org/showthread.php?t=685641)

---

