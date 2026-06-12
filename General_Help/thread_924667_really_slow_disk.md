---
title: "really slow disk"
date: 2008-09-19
forum: General Help
---

### Post by pdq on 2008-09-19
I have a 500 GB SATA drive that is just killing me.

/dev/sdc1:
 Timing buffered disk reads:    4 MB in  4.20 seconds = 975.72 kB/sec

here is my the line for that disk in fstab.
/dev/sdc1 	/media/data 	ntfs-3g	auto,gid=1002,umask=0000 	0 	0

Any ideas?  Need any other info?

---

### Post by oilchangeguy on 2008-09-19
> **pdq said:**
> I have a 500 GB SATA drive that is just killing me.

/dev/sdc1:
 Timing buffered disk reads:    4 MB in  4.20 seconds = 975.72 kB/sec

here is my the line for that disk in fstab.
/dev/sdc1 	/media/data 	ntfs-3g	auto,gid=1002,umask=0000 	0 	0

Any ideas?  Need any other info?

"any ideas? need any other info?" yep, how about you tell us what it is you're trying to do. details, details, details.

---

### Post by pdq on 2008-09-19
Correction: this is an IDE drive.

I'm trying to make the disk somewhat usable.  It's taking almost an hour to copy 1GB to this disk.

EDIT: sorry for not being more explicit, but i thought this would speak for itself:
Timing buffered disk reads: 4 MB in 4.20 seconds = 975.72 kB/sec

---

