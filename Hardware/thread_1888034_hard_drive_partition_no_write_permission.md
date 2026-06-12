---
title: "hard drive partition no write permission"
date: 2011-11-28
forum: Hardware
---

### Post by Grumpywolfe on 2011-11-28
Hi all

This was my first upgrade that I went though and for the most part things went find I upgraded from 11.04 to 11.10. Then one day I go to back up some date and find the the partition that I use is not able to me I do not have write permission to store file there any more and am not the owner of the drive. I have been using Linux for a while now and this should not be problem for me but I just not finding the answer if some one can point me in the right direction I would appercite it.

---

### Post by Mark Phelps on 2011-11-29
Is the partition you use for backup formatted NTFS?

If so, the problem is most likely to be the filesystem driver.  With earlier versions of Ubuntu, you could have BOTH ntfsprogrs and ntfs-3g.  But with 11.10, these are incompatible.

Check to see if ntfsprogs is installed, and if so, remove it and replace it with ntfs-3g.  That should solve your permissions problem.

---

### Post by Grumpywolfe on 2011-11-29
the drive in question is in ext3

---

