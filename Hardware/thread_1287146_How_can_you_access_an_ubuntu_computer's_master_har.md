---
title: "How can you access an ubuntu computer's master hard drive on windows vista?"
date: 2009-10-09
forum: Hardware
---

### Post by cooltuyul on 2009-10-09
My ubuntu somehow had an unclean shutdown, and i cannot start it up. i tried taking out the hard drive (sata) and putting it in an external casing and tried to access it through a windows vista. it recognized it, but had no drive letter nor could put one and i couldn't access the drive because it didnt show up under "computer".

---

### Post by Dark_Stang on 2009-10-09
Yup, windows doesn't support Linux filesystems natively. There may be some add-ons available to do that. Search google for ways to mount your filesystem (whatever it is, ext3, ext2, etc) in Windows. Also, Linux doesn't just not start if it doesn't shut down normally. Did anything else happen? System updates maybe?

---

### Post by oldfred on 2009-10-10
I do not think even if you install the windows driver for reading ext3 partitions you can do any repairs.

You should load a liveCD or one of the many repair live CD's to either force a filecheck fsck or use testdisk to check the partitions.

Re: Linux technician tools
make one each of these and use the most up-to-date version.
[http://www.ubcd4win.com/](http://www.ubcd4win.com/)
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
Also
Parted magic, gparted, any live linux, supergrub

---

### Post by damis648 on 2009-10-10
There is a Windows driver for Ext2 (which works on Ext3 and Ext4 as well because those are backward compatible with Ext2) that you can download [here]("http://www.fs-driver.org/").

---

### Post by cooltuyul on 2009-10-11
> **damis648 said:**
> There is a Windows driver for Ext2 (which works on Ext3 and Ext4 as well because those are backward compatible with Ext2) that you can download [here]("http://www.fs-driver.org/").

Thanks damis it worked, i just reinstalled 9.04. now all i have to do is figure out the wireless internet.

---

