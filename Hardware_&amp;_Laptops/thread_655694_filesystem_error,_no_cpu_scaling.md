---
title: "filesystem error, no cpu scaling"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by Nzer24 on 2008-01-01
From out of the blue, my filesystem was messed up...

It will boot, and runs fsck, which tells me that 1.6% of files aren't contiguous. It will boot up completely, but only if I go through recovery mode and use telinit to boot X. Then it tells me that CPU scaling is unsupported, although it was before. The system seems fine, but I think it might have messed up some system files...

I have a large hard drive, which has a windows partition large enough to hold my home files, but I can't use a liveCD because of video card issues (I'll explain if necessary). How can I fix this?

Is this a sign that my hard drive is breaking, or is it just a problem made by linux?

Also, what does the 1.6% of files not being contiguous mean in relation to the error?

---

### Post by Nzer24 on 2008-01-02
Well, good news. It seems that the error has disappeared. Regardless, is this a problem I should be worried about, and why did it fix itself?

---

### Post by jespdj on 2008-01-02
The message about the files not being contiguous just means that you have a small amount of fragmentation in the file system. The Linux ext3 filesystem is usually very good at keeping files unfragmented (much better than Windows FAT and NTFS file systems), but if the disk gets more and more full, some fragmentation could occur. It's not really a big problem and it doesn't mean that there's an error.

Maybe you had a temporary harddisk error. How old is your harddisk, and how many hours do you have it switched on each day? Make sure you backup important data, this might be the first signs that your harddisk is getting older, and one day it might suddenly die.

---

