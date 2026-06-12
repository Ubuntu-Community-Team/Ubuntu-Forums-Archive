---
title: "Detect scsi channel by uuid or mount point"
date: 2013-09-16
forum: Hardware
---

### Post by _2009 on 2013-09-16
Hi,

I hope someone can help or advise if it is not possible!

Our file server (Ubuntu 12.04) has a removable drive that I backup to, rotating the disk every night.
I have given both of these disks the same UUID to avoid any problems on a reboot. 
I have a script that does the backup via crontab and at the end of the day it calls:
```
umount /mnt/removable;
echo "scsi remove-single-device 1 0 0 0" > /proc/scsi/scsi;
```
Now the problem comes on a reboot as the removable disk is not always detected on scsi channel 1. The sata port it is plugged in to doesn't change.

Is there a way to detect the scsi channel by a disk's uuid or mount point? I would like to add this to my script so I don't stop the wrong drive. This has happened twice already, leaving me with degraded arrays that I need to rebuild!

Any pointers gratefully received.

Thanks,
_2009

---

