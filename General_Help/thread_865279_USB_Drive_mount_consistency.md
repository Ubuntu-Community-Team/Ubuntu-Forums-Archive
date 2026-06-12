---
title: "USB Drive mount consistency"
date: 2008-07-20
forum: General Help
---

### Post by srwilde on 2008-07-20
Hello,

I'm running Hardy with all recommended updates.  I boot from an internal SATA drive.  I have three external USB drives.  I've specified in my /etc/fstab for the three USB drives to mount at boot time.  The problem is that the USB drives don't scan in at a consistent device name.  This causes the mount commands to fail or for devices to be mounted at incorrect locations.

snippet of /etc/fstab
...
/dev/sdb1	/media/backup	ext3	rw	0	0
/dev/sdc1	/media/music	ext3	rw	0	0
/dev/sdd1	/media/backup2	ext3	rw	0	0
...

Any ideas?

Thanks,
Steve

---

### Post by Elfy on 2008-07-20
Try using UUID instead - plug them in and run

```
sudo blkid
```

that will get the UUID for each drive - replace the /dev/sdb1 in fstab  with UUID for it.

I assume they are plugged in when you boot - if they're not I'm not completely sure if that would work though.

---

### Post by srwilde on 2008-07-20
Doh!  Of course.  That got it.  Many thanks.

---

