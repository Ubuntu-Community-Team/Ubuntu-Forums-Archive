---
title: "External HP DVDRW problems"
date: 2006-09-26
forum: Hardware &amp; Laptops
---

### Post by tarlos25 on 2006-09-26
I've been having some issues with my external USB HP dvd740e drive.  First, if I put an audio CD in, it will play in Sound Juicer, but nothing else can find it.  Not a big deal, since I've got another drive (DVD ROM) internal to the computer that works fine for this purpose.

Today, I tried burning some data discs, and found that Nautilus would burn the disc, but hangs up at the end.  The first disc burned correctly, and after I "cancelled" the burn and tested the disc in another computer, the disc works fine.  I proceeded to burn a second disc (exact same data, just another copy), and repeated the procedure.  This time, after cancelling the burn, I could not eject the CD.  After trying various methods to eject the CD, I rebooted the computer.  Again, the CD would not eject using the button on the drive, but on the desktop, the icon had changed to the title of the disc instead of Blank Disc.  At this point, I was able to right click the icon and click eject, and it gave me the disc.  So I first thought Nautilus was having problems.  I installed k3b and gnomebaker, and neither of these programs could find the CD drive at all.

The drive is not listed anywhere in /etc/fstab, but in /proc I can find the correct information for it.  It is at /dev/scd0.

My /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /code           vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb3       /data           vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

/dev/hdc is the internal DVD ROM, and I have tried duplicating (with slight variations) its fstab entry for /dev/scd0, with no luck.

The drive works in Windows, so I know the drive is functional.  Does anyone have any suggestions for making this drive functional under Ubuntu?

---

