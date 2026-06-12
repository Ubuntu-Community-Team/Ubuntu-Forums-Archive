---
title: "performance of large number of folders in EXT3"
date: 2008-07-01
forum: Hardware
---

### Post by pompeyjohn on 2008-07-01
Hi there,

I am migrating a very large number of files and folders from an NTFS drive to EXT3. 

Navigating this hierarchy in windows was at times, painful. A short term fix was to use multiple sub-folders so there wasnt too many folders at each level. Ideally, all folders would have been at the same level.

Will EXT3 be any better than NTFS in this respect?

In short, can I place all folders at one level without a large performance hit.

Thanks in advance,
John

---

### Post by arsenic23 on 2008-07-01
I can't say for sure --- but for me, I can notice a large difference in folder response of directories with a large number of files/folders between ext3 and NTFS

---

### Post by Tomatz on 2008-07-01
> **pompeyjohn said:**
> Hi there,

I am migrating a very large number of files and folders from an NTFS drive to EXT3. 

Navigating this hierarchy in windows was at times, painful. A short term fix was to use multiple sub-folders so there wasnt too many folders at each level. Ideally, all folders would have been at the same level.

Will EXT3 be any better than NTFS in this respect?

In short, can I place all folders at one level without a large performance hit.

Thanks in advance,
John


The gui (nautilus etc) would be the only thing that would slow things down. In midnight commander opening the top level directory would be pretty much instantaneous (within reason).

---

### Post by pompeyjohn on 2008-07-02
Thanks All :)

---

