---
title: "Problems with cloning HDD by dd"
date: 2013-11-26
forum: Hardware
---

### Post by imrunningoutofname on 2013-11-26
I've got a 2TB WD Elements (originally formatted in windows) that suddenly became unitialised.  I suspect it's failed and is unrecoverable, but hey, I'll try anyway.

My plan is to clone it, then attempt recovery on the clone.  That should prevent a recovery attempt actually damaging the drive further.

I was using dd to copy it via USB 2.0 and it was only transferring at 2.7MB/s.  After a full day and only 150gb I decided I wasn't keen on waiting a fortnight for the task to finish.  So I connected it via SATA instead.
Now it's transferring at 25.6kB/s instead......any idea why it's going so ridiculously slow?

Also, pretty much every few lines reads: 

> dd: reading'/dev/sda'; input/output error

Given that, is that likely to mean there is absolutely no point whatsoever in going down this path?  Or is it still potentailly recoverable (eg by recovering the MBR or some such)?

---

### Post by VMC on 2013-11-26
Try using Testdisk to see if it can make heads or tails out of the drive. It might be a futile attempt, but at least you'll know.

---

### Post by imrunningoutofname on 2013-11-26
Yeah, couldn't get anything from Testdisk

---

### Post by varunendra on 2013-11-27
Doesn't look like any further attempts are going to help, but just FYI, ddrescue is much better and faster than dd in imaging corrupt partitions. It is usually run once in forward, once in reverse direction to complete the image of a partition/drive, and the resultant image is complete in itself unlike the one created by dd in case of I/O errors.

A short description of how to use it : [http://ubuntuforums.org/showthread.php?p=12697693](http://ubuntuforums.org/showthread.php?p=12697693)

---

