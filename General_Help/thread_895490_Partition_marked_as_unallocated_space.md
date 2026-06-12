---
title: "Partition marked as unallocated space"
date: 2008-08-20
forum: General Help
---

### Post by kseise on 2008-08-20
I am running Hardy 64bit.  I recently tried to use the suspend feature on my desktop.  On resume, the system came up as if it was a full reboot.  When it came up, my /home directory was missing.  After poking around with a live CD, I found that the partition was listed as unallocated space.  My disk was partitioned as:
sdb1 100 GB NTFS
sdb2 400 GB ext3

Now only the NTFS shows up.
I ran testdisk and it saw the ext3 parition, but when I told it to write, nothing happened and I can't seem to recover the partition.  Is there a way to recover it?

---

