---
title: "Best File System for a Backup Partition that can be read by Linux, Windows and BSD"
date: 2012-11-05
forum: Hardware
---

### Post by just_ken_here on 2012-11-05
I want to make back up partition in a drive. I have NTFS in my mind.
So it can be read by Windows.

Are there any better or newer partition --efficient, relatively safe, fast and reliable that you can recommend ?

Thx.

And that GParted or some other software can partition it

---

### Post by ahallubuntu on 2012-11-05
NTFS.  While there are ext drivers of a sort for Linux, I have found them very lacking and not to be relied on.

ntfs-3g is pretty mature - I've used it for years in Linux and few issues with it, none with reliability.  The worst problem I have found in Linux is that very large files (GB+) take a lot of CPU time to write especially and take longer to copy than to a straight ext partition.

I've not used the newer versions of FreeBSD, but I assume ntfs-3g will work just as well there.

---

