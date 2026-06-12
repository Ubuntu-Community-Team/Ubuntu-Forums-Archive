---
title: "Disk Space Analyer Reporting incorrect numbers"
date: 2009-02-10
forum: Hardware
---

### Post by pbennett45 on 2009-02-10
So I switched over from Fedora.  I installed Ubuntu on a clean-slated 150GB drive.  Mounted the old drive that had fedora on it and copied over the files I wanted to save (filled most of the 150GB drive.. like 85% or so).  Formatted the old fedora drive to use as my main data drive (it was a 250gb drive).  Copied everything back to the 250gb drive and deleted it from the 150gB drive (my main ubuntu installation).  Now when I run disk usage analyzer, in the details it's reported correcting showing the the root file system / is taking up 23.4GB.  However, up top, where it says "Total capacity 107.9GB" it says (used: 95.2 GB available: 12.7 GB) which is reminiscent of BEFORE I deleted the backups from the other drive.  I tried forcing a fsck on reboot and that didn't fix the problem.  The .Trash folders are empty - and besides, the usage analyzer should have shown that in the detail anyway.  It seems like the filesystem is mangled, but fsck isn't doing the trick.  Anyone seen this before?  Anything else I can try?  I've already installed a few favorite apps and I don't really want to clean-slate the drive again.  Thanx!

---

### Post by lavinog on 2009-02-11
I had noticed this today also when backing up my laptop.
I figured it had to do with the sum of all partitions.
Either way it isn't your system, it is disk usage analyzer.
df should give you the correct numbers

---

### Post by lavinog on 2009-02-11
See what filesystems are being totaled in the preferences

---

### Post by pbennett45 on 2009-02-11
I'll check it when I get home, but I'm pretty sure df gives me the incorrect number.  Also shows that incorrect number in nautilus.  I'm tempted to just back up any data that's not already on a different drive, and drag a bunch of big files onto the drive.. see what happens... if it lets me write the full amount to the disk, i don't really care what it SAYS the utilization is.  If it doesn't then I may just have to reformat and reinstall... argh...

---

### Post by pbennett45 on 2009-02-11
yea.. definitely not the problem...  df reports the same 93% used or whatever... under preferences same thing even if i make sure only /dev/sda1 is selected.

---

### Post by lavinog on 2009-02-11
what did you use to delete the files?
I remember noticing that if I deleted a folder in disk usage analizer, it would put it in a trash folder that was different than the ubuntu trash folder
what if you tried:
```

sudo du --max-depth\=1

```
in the root of the affected mount point.

---

