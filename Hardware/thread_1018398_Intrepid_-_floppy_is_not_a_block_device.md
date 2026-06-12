---
title: "Intrepid - floppy is not a block device"
date: 2008-12-22
forum: Hardware
---

### Post by gordon3913 on 2008-12-22
I could not mount my floppy drive.
After checking the forums I added "floppy" to the end of /etc/modules
It is still coming up with "/dev/fd0 is not a block device"
Can someone please help.

---

### Post by gordon3913 on 2008-12-28
I went back to basics and changed fstab to:-

/dev/fd0  /media/floppy0  rw,user   0  0

My floppy drive now works again.

Can the administrators of Ubuntu please fix this annoying problem.
It makes for very frustrated users.
:)

---

