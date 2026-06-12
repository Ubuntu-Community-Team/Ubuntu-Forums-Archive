---
title: "Dual HDD with a &quot;new&quot; OS on second"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by valkarin on 2007-01-02
I am running Ubuntu 6.06 and I would like to add a second HDD.  I have read the how-to and all is well sofar.  But I need to partition the second drive in two.  The big partition (15GB) will be used for storage, but the little one (3GB) will be used to install DOS (don't ask).  How can I do this?  Also, how can I boot into DOS at startup?

---

### Post by budgie9 on 2007-01-02
Being as you wish to use DOS then why not use the DOS tools to create the partitions
Use the FDSIK tool on DOS disks. Answer (Y) yes to the first option. Then set the disk up as you wish, using FDISK
If you set the disk to Win32 which you will have done answering Yes, then you can save both your files from DOS and the files from Linux on it. That will depend on the version of DOS you are using. 
You maybe able to use Gparted to do the same things, But I don't know if will work for DOS settings
As to setting DOS to be active I am not sure, I would thing some of the posts re Grub will help you there.

---

