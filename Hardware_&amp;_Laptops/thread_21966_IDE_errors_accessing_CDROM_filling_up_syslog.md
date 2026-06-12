---
title: "IDE errors accessing CDROM filling up syslog"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by Levander on 2005-03-24
I've got errors accessing my CD drive filling up my syslog.  I got a few hundred megs of these messages being repeated:

Mar 24 22:20:06 bread kernel: hdd: ATAPI reset complete
Mar 24 22:20:06 bread kernel: hdd: status error: status=0x50 { DriveReady SeekComplete }
Mar 24 22:20:06 bread kernel: hdd: status error: error=0x50LastFailedSense 0x05


hdd is the CD drive.  It's actually a CDRW drive.  While these errors are being printed into syslog, nothing I can do to eject the drive, even though it's not mounted.  Not even hitting the eject button on the drive works.

I can put the Warty Installation CD in that drive and boot the computer fine off it.  Take the CD out, reboot into Ubuntu, put the CD back in, and mount and access the drive then just fine.  However, not to much later (like maybe an hour?) something goes haywire.  I can't eject the drive again and the messages start filling up syslog again.

Any ideas?

---

