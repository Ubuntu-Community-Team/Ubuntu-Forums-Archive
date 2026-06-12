---
title: "USB external drive ext3 very slow delete"
date: 2008-12-01
forum: Hardware
---

### Post by DrJohn999 on 2008-12-01
Using 8.10 server; 320 GB WD external USB drive, single partition formatted ext3.

I use two of these drives, alternating them, for backups, storing 6 or 7 large *.tar.gz files archival from backuppc, typically from 65 to 73 % of the drive capacity, so perhaps 35 GB / file on average, from 16 to 97 GB each on the most recent set. The write speed is OK, taking perhaps 10 hr to complete an archive operation (maybe 6 MB/s). May be CPU limited to some degree as well, since it runs near 100% when these jobs are queued up.

What's strange (to me anyway) is that it takes almost 10 minutes to delete the six or seven files (from a terminal session). I realize that ext3 is going to be busy keeping up with the changes to the drive as they happen, but is there any way to speed up deletes of such large files? Maybe a different file system (xfs, jfs)?

Thanks,

DJ

---

### Post by JNelson on 2008-12-02
Ext3 uses a classic block mapping technique which is not good for large files. THat is what explains your long file deletion times. Try an extent based filesystem like jfs.

---

### Post by DrJohn999 on 2008-12-07
Thanks, JNelson, that did the trick. The deletion time now is not perceptible.

-- DJ

---

