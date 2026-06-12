---
title: "cd-rom mount error SOLVED"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by 8rdx on 2007-12-08
I had an issue with mounting cd's... Music cd's would run just fine, but when I put a data cd in it would not mount (no cd icon or Nautilus window on desktop) I could mount it through
Administration|Disks|CDROM|Partitions,
but even sudo mount in the shell would not work - I kept getting error
"mount: line 11 in /etc/fstab is bad
can't find /dev/hdc in /etc/fstab or /etc/mtab"
fstab LOOKED fine...:confused:

BUT

I had recently used "NTFS Configuration Tool", which rewrote fstab.
When I compared the old with the new, I found it had inserted a space between
/media and /cdrom0

Removed the space and all is well :)

Why did NTFS Config do that? I have no idea, but the moral of the story is spaces in the wrong places are BAD.

---

