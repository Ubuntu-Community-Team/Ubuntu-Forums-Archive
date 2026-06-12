---
title: "Does Ubuntu 5.10 support JFS?"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by dreadthenight on 2005-11-08
I just installed Ubuntu 5.10 from CD after seeing on Google that it supported the JFS filesystem.  After mounting my JFS drive however, the "Disks" application shows the filesystem as unknown?

When I mount the same drive in Knoppix, it is seen as JFS.

Thanks for any advice!

---

### Post by dreadthenight on 2005-11-08
[QUOTE=dreadthenight]I just installed Ubuntu 5.10 from CD after seeing on Google that it supported the JFS filesystem.  After mounting my JFS drive however, the "Disks" application shows the filesystem as unknown?

When I mount the same drive in Knoppix, it is seen as JFS.

Thanks for any advice![/QUOTE]

Solved, I got some great advice on the IRC channel and reviewed dmesg output for errors.  I had the drive mounted behind a write-block device, and it appears if you try to mount a drive (by default in Ubuntu read-write) like this, the mount will fail.  You have to force the mount to be read-only if a write-block device is involved.  I had just assumed if a regular mount couldn't write to a drive, it would just revert to read-only.

---

