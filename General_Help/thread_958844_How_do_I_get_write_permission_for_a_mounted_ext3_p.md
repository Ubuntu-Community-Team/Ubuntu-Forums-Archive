---
title: "How do I get write permission for a mounted ext3 partition"
date: 2008-10-25
forum: General Help
---

### Post by bcasanov on 2008-10-25
Hi,

I am using a live CD right now, and I would like to copy and paste files onto a mounted ext3 partition.  When I try to paste the files, I do not have the permission to do so.  How can I get write access on the partition?

---

### Post by lswb on 2008-10-25
If you just don't have proper user permissions for writing to the partition, 
try running your file browswer with gksudo, i.e. for nautilus,

gksudo nautilus

If the error message says something about the partition being mounted read only, you can remount it rw like so:

sudo mount -o remount -o rw /path/to/mountpoint

---

