---
title: "Ubuntu vs fstab: Where is my DVD-RW drive?"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by keithjr on 2006-11-05
OK, here's the background.  I used to have two secondary IDE drives: an old CDRW drive and a more recent DVD-RW drive.  Both were connected when I installed Dapper.  I've had no problems with them; they both automounted fine.  Recently, I removed the older cd drive, but that isn't terribly important.  Because everything was working fine, I never did much poking around in fstab.  

However, I recently installed Cedega, and am having a TERRIBLE time getting it to coordinate multi-CD installs.  I discovered that it was not seeing the dvd drive in its Mount menu, and decided to check fstab.  Lo and behold, there was no entry for my dvd drive in there at all.  

Here's my current fstab, although it isn't much use.

```

proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /boot           ext3    defaults        0       2
/dev/hda3       /home           ext3    defaults        0       2
/dev/hdb1       /mnt/hdb1       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       none            swap    sw              0       0

```

There used to be an entry for /dev/hdd which mounted to /media/cdrom0, but I'm assuming that was for my old CD drive, and removed it.  Even with it gone, Ubuntu still manages to automount when I put a CD in the drive, mounting to "/media/dvdrecorder".  

The Ubuntu Disk Manager correctly sees the DVDRW drive as /dev/hdc, and identifies its mount point as /media/dvdrecorder.  My question is, why is there no accompanying entry for this device in /etc/fstab?  This seems like it would be of grave importance.  

To make Cedega work correctly, could I add a matching entry to fstab?  On that note, what would I proper DVDRW drive entry look like in fstab?  I always seem to mess the options up when I fiddle with that file myself...

Thanks!

---

