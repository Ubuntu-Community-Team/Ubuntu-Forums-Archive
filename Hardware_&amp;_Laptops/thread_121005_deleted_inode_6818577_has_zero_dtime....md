---
title: "deleted inode 6818577 has zero dtime..."
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by Tiede on 2006-01-24
Ok, I am running breezy on a newly bought laptop (less than a month old, actually).
I have this problem on every 3rd/4th or 5th boot. I am suspecting badblocks as the source of the problem, but a quick ```
sudo e2fsck /dev/hda5 -cc -C 0 
``` using the live cd does not complain about any badblocks.... I did not want to -c it (destructive read/write test unless I was sure it was badblocks... so I used -cc instead). If someone could give me an explanation of the problem in non-geek language and if possible tell me ow I could go about fixing it?
Here is the error message I get:
```
ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5
e2fsck 1.38 (30-Jun-2005)
/: recovering journal
/ contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1868577 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong for group #198 (19594, counted=19595).
Fix<y>? yes

Free blocks count wrong (6130570, counted=6130571).
Fix<y>? yes

Inode bitmap differences:  -1868577
Fix<y>? yes

Free inodes count wrong for group #7 (16335, counted=16336).
Fix<y>? yes

Free inodes count wrong for group #114 (14298, counted=14299).
Fix<y>? yes

Free inodes count wrong (3316072, counted=3316074).
Fix<y>? yes


/: ***** FILE SYSTEM WAS MODIFIED *****
/: 108182/3424256 files (0.9% non-contiguous), 705078/6835649 blocks
ubuntu@ubuntu:~$

```

*Wanted DEAD or ALIVE!*
-> Help  <-
Prize: 1 coffee bean :D

---

### Post by Tiede on 2006-01-30
I reinstalled three days ago, and it stopped doing that. The fs was the problem after all and not my HD. This thread has thus become obsolete. Any mod reading this can delete it anytime since I was the only one in it in the first place. Thanks. And sorry for the wasted space.

---

