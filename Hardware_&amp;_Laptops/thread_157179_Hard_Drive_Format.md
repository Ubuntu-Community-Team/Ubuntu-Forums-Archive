---
title: "Hard Drive Format"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by Razorback on 2006-04-08
I have wiped Windows off of another drive in my system and have turned it into a storage disk.  My question is what format (vfat, ext2, ext3, etc...) is best for this?  Right now it is vfat.

---

### Post by DoktorSeven on 2006-04-08
If only Linux will be accessing it, ext3 is fine.  If you think you'll ever need to access it with Windows again, go vfat.

---

### Post by Razorback on 2006-04-08
Thanks.

---

### Post by louis_nichols on 2006-04-09
you can go ext2 and use it both in windows and Linux. Linux is native, in win you can use [EXT2IFS]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

I'm saying this because fat32 has a famous file size limit of around #GB, which means that if you ever need to deal with DVD isos for example, it won't be able to help you. ext2 is able to go beyond that limit and is even faster.

---

### Post by louis_nichols on 2006-04-09
EDIT: ooops, double post. Sorry! Wasn't my fault, though. Does anybody know how I can delete it?

---

### Post by louis_nichols on 2006-04-09
GRRR 3 times, even! Now they'll say I'm a spammer! :((

---

