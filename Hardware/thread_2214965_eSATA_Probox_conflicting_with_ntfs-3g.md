---
title: "eSATA Probox conflicting with ntfs-3g"
date: 2014-04-04
forum: Hardware
---

### Post by LoREZ on 2014-04-04
Hi,
I'm getting random disconnects and phantom mount points when using ntfs-3g in my fstab with an external eSATA enclosure.  It will say "[volume label] connected" (when it was already connected), and lock the screen for 10 or 20 seconds, while allowing work behind the scenes (I can pause video, type, etc).  I'm forced to use ntfs-3g in my fstab because otherwise PlexMediaServer will not see my ntfs partitions (which I have to use because of win7 partition).  I feel that I can kill this problem if I can get the automount feature to ignore the enclosure, but I'd like to keep the feature for other random flashdrives, etc. that I plugin.  I know it's not the hardware, since it works fine in both Windows and without the ntfs-3g option in my fstab.  Any ideas?  Thanks in advance...

---

### Post by frostschutz on 2014-04-05
That doesn't make much sense. ntfs-3g doesn't really care what kind of medium it is, as long as it works reliably.

Anything in the kernel log / dmesg when the issue occurs?

---

### Post by LoREZ on 2014-04-09
Thank you for your reply, frostschutz.  After looking further, it seems this only really happens in Cinnamon, although both Nemo and Nautilus show the phantom mount points, which I'd still like to solve.  It is more than a visual annoyance, as I often click on the phantom drive, which inevitably wastes time or even causes a slowdown as the computer tries to figure out why it can't access the drive.  I don't know if I'm wrong in thinking this, but it seems that since it's a program and/or environment causing the disruption then kernel logs might not be very helpful, and I had trouble finding the appropriate logs besides.  If you or anyone else still thinks the kernel logs would be helpful, I'll try and capture some at the time of the interruption.  In order to get work done, I've been running KDE for a bit now.

---

