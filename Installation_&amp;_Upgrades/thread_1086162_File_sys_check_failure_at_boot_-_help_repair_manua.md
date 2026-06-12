---
title: "File sys check failure at boot - help repair manually"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by omskates on 2009-03-03
I have recently extended my /home partition into unallocated space ext3 towards the end of the HD while retaining a small unallocated to the very end.  The file system check fails at boot up though allows me to enter gui <[ctrl]D> OK

Here is the log of which I have no experience repairing manually, any tip would be much appreciated.  Thanks!

Log of fsck -C3 -R -A -a 
Tue Mar  3 16:37:15 2009

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=55d36f34-20c5-41d4-9f6b-6cc9c990098e'

/dev/sda5: clean, 44/16288 files, 18429/46186 blocks (check in 2 mounts)
/dev/sda8: clean, 48080/855120 files, 2553366/3417820 blocks
/dev/sda6: clean, 8847/225280 files, 381548/899608 blocks
fsck died with exit status 8

---

### Post by Mark Phelps on 2009-03-05
Looks like the UUID of one of your mounted partitions has changed such that the one in your fstab is no longer valid.

You can run an fsck without the -a option to avoid reading fstab and, if you can then boot into Ubuntu, you can use the "sudo blkid" command to get the UUID list of your partitions, manually edit the contents of fstab to correct the invalid UUID, and then to a "sudo mount -a" to confirm that the modified file is correct.

---

