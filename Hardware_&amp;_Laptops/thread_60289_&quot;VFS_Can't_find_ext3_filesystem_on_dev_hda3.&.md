---
title: "&quot;VFS: Can't find ext3 filesystem on dev hda3.&quot;"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by elempoimen on 2005-08-27
I get the following error on boot:

"VFS: Can't find ext3 filesystem on dev hda3."  Admittedly, that makes sense, because hda3 (my Ubuntu / drive) is formatted using ReiserFS 3.6.  And the system boots without issue--I'm just wondering what I can do to correct the error.  fstab reads "reiserfs" for hda3.

---

### Post by shof2k on 2005-08-27
I get the same sort of message but on my /dev/hda2.  I also have the partition setup as reiserfs instead of ext3?  I know fstab is ok, but does VFS need 'tweaking' somehow?

---

