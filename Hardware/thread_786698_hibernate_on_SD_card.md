---
title: "hibernate on SD card"
date: 2008-05-08
forum: Hardware
---

### Post by flygin on 2008-05-08
Is it possible to hibernate to a SD card? And is it any faster than the hard drive?

I tried it, created a swap partition on a 2GB SD card and changed /etc/fstab to point only to the swap on the SD card but it did not work. 

any help?

---

### Post by schmolch on 2008-05-08
Is it faster, are you kidding?
Class 6 refers to 6MB/s read-speed and writing is much slower.

---

### Post by eldragon on 2008-05-08
for the love of god dont set a swap partition on flash media.
they are not expected to do extensive read/write access.
your media will start to fail sooner.


hope i cleared that up :D

---

### Post by flygin on 2008-05-09
OK, we can close this thread!

Would be nice to find a way to speed hibernate...

---

