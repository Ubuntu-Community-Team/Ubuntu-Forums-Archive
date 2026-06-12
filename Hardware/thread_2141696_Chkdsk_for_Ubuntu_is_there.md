---
title: "Chkdsk for Ubuntu is there?"
date: 2013-05-03
forum: Hardware
---

### Post by Enddoc on 2013-05-03
Please reply, anyone.

---

### Post by Mark Phelps on 2013-05-03
Don't understand your question ...

If you mean, is there a way to run CHKDSK from Ubuntu, no, there is not.  There is ntfsfix, but as their website claims:

> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. 

What it does is mark the NTFS partition as "dirty" so that when MS Windows sees it again, it will automatically run CHKDSK against it.

IF you mean is there an equivalent for Linux filesystems, use fsck.  Type "man fsck" (in a terminal) to see the options. I believe there is also a way to do a filesystem check using the Disk Utility -- but you will probably have to run this from a LiveCD or LiveUSB -- as you can't run a check on a filesystem that is in use.

---

### Post by prodigy_ on 2013-05-03
You should use forum search.

[http://ubuntuforums.org/showthread.php?t=2141243](http://ubuntuforums.org/showthread.php?t=2141243)
[http://ubuntuforums.org/showthread.php?t=2141483](http://ubuntuforums.org/showthread.php?t=2141483)

---

