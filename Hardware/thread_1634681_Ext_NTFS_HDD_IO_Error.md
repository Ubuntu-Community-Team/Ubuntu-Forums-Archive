---
title: "Ext NTFS HDD I/O Error"
date: 2010-11-30
forum: Hardware
---

### Post by nevafuse on 2010-11-30
Running latest ubuntu (command-line) on an older hp laptop.  I have a usb external iomega 1tb harddrive attached.  I use the drive to store all my video files that I stream to my xbox daily.  I recently updated fstab to mount the drive using the line below...

```
/dev/sdb1	/media/iomega	ntfs-3g	defaults	0	0
```

(Before I was using another ntfs type that was extremely slow & read that I should start using "ntfs-3g" instead.  Now once a day I get an input/output error when I try to read from the drive.  It won't let me umount it (says another process is using it).  If I reboot it hangs on the ubuntu loading screen saying it is waiting on /dev/sdb1 to be ready.  If I unplug & re-plug in the harddrive it fixes the issue & ubuntu will finish booting.

I'm debating whether it is the harddrive or the new "ntfs-3g" type.  I might try to partition half the drive to ext3 (to see if it is the type or drive that is having issues).  I was curious if anyone else had experienced this issue & knew of a quick fix.  I'd prefer to keep it NTFS, but will convert if its necessary.  Thanks.

---

