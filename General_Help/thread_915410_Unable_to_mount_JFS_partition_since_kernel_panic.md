---
title: "Unable to mount JFS partition since kernel panic"
date: 2008-09-09
forum: General Help
---

### Post by gabspeck on 2008-09-09
Hello,

Since a kernel panic last night I've been unable to mount my JFS-formatted /home partition as rw. At boot time, the console shows the messages attached in dmesg.log, the ones I think are related to this error start at line 656. fsck fails and reports the errors attached in fsck.log with the verbose (-v) switch on. I can mount the partition as read only though.

Is there anyway to fix this without resorting to copying the data to another location and reformatting the partition? Can jfs_debugfs be of any help?

Thanks in advance

---

