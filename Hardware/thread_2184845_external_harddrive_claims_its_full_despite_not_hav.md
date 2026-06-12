---
title: "external harddrive claims its full despite not having much on it"
date: 2013-10-30
forum: Hardware
---

### Post by guine on 2013-10-30
So Im trying to back up my files on an external harddrive so I can reinstall ubuntu after breaking unity and gnome and its saying its full despite not having much on it yet.  If I check properties for the whole drive it says I have nearly 500 gigs on it but when I highlight everything that it let me copy over and check its properties they only add up to about 125 gigs.  Anyone have any idea whats going on and how to fix it.
Thanks.

---

### Post by Mark Phelps on 2013-10-31
How about doing an "sudo fdisk -lu" (lowercase L, not a one) for us to see the partition formatting and usage of the drive.

---

### Post by guine on 2013-10-31
I was able to format it on a windows box and it seems to be working properly now.  Thanks

---

