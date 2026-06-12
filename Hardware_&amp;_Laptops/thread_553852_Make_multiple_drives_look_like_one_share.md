---
title: "Make multiple drives look like one share"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by djuniah on 2007-09-18
I have a few extra drives laying around and i would like to incorporate them into my media server.  My issue is that i would rather not have to split my video files onto different share directories.  I realize that I could probably just put certain folders on certain drives and symlink them at the share, but i have two small issues with that.  One being that its an organizational nightmare when trying to access the data directly on the server without using the share, and two, do symlinks even work over samba?  I was also wondering if there was some sort of software solution to simulate a RAID on multiple HDs that normally wouldn't work in RAID (for instance, a SATA drive, a regular IDE drive, and an external USB drive all together).  I do realize that that opens up the possibility for catastrophic data loss if one should fail, and a potential loss in data throughput if one drive was slower, but at this point im just kinda curious about it.

Any ideas or suggestions would be greatly appreciated.

~DJuniah

---

### Post by kidders on 2007-09-19
Hi there,

> **djuniah said:**
> I was also wondering if there was some sort of software solution to simulate a RAID on multiple HDs that normally wouldn't work in RAID (for instance, a SATA drive, a regular IDE drive, and an external USB drive all together). Why wouldn't RAID work? I don't think it's such a bad idea, personally.

---

### Post by mrintegrity on 2007-09-19
This forum post covers the basics quite nicely:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

