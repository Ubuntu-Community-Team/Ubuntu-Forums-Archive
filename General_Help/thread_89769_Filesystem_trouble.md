---
title: "Filesystem trouble"
date: 2005-11-13
forum: General Help
---

### Post by Schapie123 on 2005-11-13
Aah! I was happily cleaning up my anime partition, until suddenly I got an error while deleting some files. I got told write permissions for this device were disabled. But I couldn't find anything, thus I decided to reboot my system (well, if it does magic in windows, why not here?).
During boot I get told the filesystem in question contains errors and needs to be checked. After a few minutes a message that fsck fails to repair the errors, and it needs to be done manually.
I'm absolutely clueless about what's going on. What to do?
I tried running fsck manually, but somehow I can't unmount the partition before doing so. As far as I know I have no programs running which use the partition. Will I get into trouble if I run fsck anyway? And will it help me to get rid of this problem?
I am using using 2.6.14-ck1 kernel, if that's important.

---

### Post by andrewsawyer on 2005-11-15
Just a thought - # out the line that contains the partition in the /etc/fstab file and then reboot again.  This way, it should never even get mounted.  You can then run fsck while the partition is in its unmounted state.

Then once done, just remove the # from the /etc/fstab file.

---

