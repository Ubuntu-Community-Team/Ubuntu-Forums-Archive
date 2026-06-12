---
title: "How can I tell which drive in RAID is failing?"
date: 2009-01-08
forum: Hardware
---

### Post by jelevin on 2009-01-08
I think that I have a failing disk drive, but I don't know how to tell which one.  Ubuntu 8.10.  Reboot failed, with suggestion to run fsck manually on my Raid-1 array.  This ran with a ton of errors that presumably were fixed.  After the next reboot the raid status was reported to be something like 98.5% for a bit.  Now I see this message in syslog:  

*Jan  8 18:17:08 computername kernel: [27946.849051] EXT3-fs error (device dm-1): htree_dirblock_to_tree: bad entry in directory #23248900: directory entry across blocks - offset=0, inode=526135583, rec_len=18256, name_len=83*

I assume that one of the mirrored disks is failing, but how can I tell which one?  I would appreciate any help.

---

### Post by Cracauer on 2009-01-08
This is not a disk error, it is a filesystem format error.

This can be a hardware error other than a failing disk, such as bad memory, unverified overclock or the like.

Either way, your actual disk do not show errors at this time (unless you omitted error messages from syslog).

---

