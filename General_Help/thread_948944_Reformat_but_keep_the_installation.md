---
title: "Reformat but keep the installation"
date: 2008-10-15
forum: General Help
---

### Post by smfaisalabbas on 2008-10-15
Hello,

Is there a way I can reformat my hard drive but keep my Ubuntu and the programs installation intact?

What I want is to convert my hard drive partitions from ext3 to riserfs.

Thanks

Faisal

---

### Post by Pro-reason on 2008-10-15
I believe that conversion between ext2 and ext3 is possible without harming the contents of the filesystem, but other conversions involve loss of all data.  That's why “format” has ended up being used as a synonym for “delete all contents”.

You need to back up the contents of the drive, reformat, and then restore.  It's a bit of a hassle though.

I advise you to wait until Intrepid Ibex comes out, and then use that as an opportunity to format your drive and upgrade your system.

There's no rush.  I personally use ReiserFS, and I can tell you that you will not notice any real difference between it and ext3.

---

### Post by C.S.Cameron on 2008-10-15
At the least you can save your home folder to another partition or drive and copy it back after you build a system on the reiserfs partition.
All your settings will be the same, and anything you installed under wine will be there.
Reiserfs seems to speed up my bootable flash drive a bit, but I could not swear to it.

---

