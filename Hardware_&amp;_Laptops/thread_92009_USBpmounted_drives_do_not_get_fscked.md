---
title: "USB/pmounted drives do not get fscked"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by radbrad on 2005-11-18
Hey...

After a directory decided to turn into a zip file that had no bearing on the original directory, and I decided to fsck my usb drive, i noticed that it had not been fscked in 78 mounts, even though dumpe2fs says:
```
Maximum mount count:      32
```
So...I can only be led to believe that it is a problem in pmount, but i am not one hundred percent sure, and if it is an intended function (for e.g. it may be bad to fsck flash sticks???), or just an oversight.

Was just wondering if anyone had anything insightful to say about all of this?

---

