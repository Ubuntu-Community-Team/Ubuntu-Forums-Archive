---
title: "Mouting a backup hard drive"
date: 2009-03-16
forum: Hardware
---

### Post by grimm08 on 2009-03-16
I am going to install a new hard drive to backup both my windows and Ubuntu partition since I run a dual boot system.  Is there a way to mount just one partition of the new hard drive or do I have to mount the whole hard drive?

---

### Post by taurus on 2009-03-16
It depends how many partitions you have on that harddrive.  If you have only one, then you have to mount that one.  But if you have more than one, then you can choose which partition you want to mount from Ubuntu.  You do not have to mount all of them if you don't want to.

---

### Post by ajgreeny on 2009-03-16
I would also suggest you have two partitions, firstly, ext3 for ubuntu, as it will make life a bit easier for you in terms of permissions and owners etc etc, particularly if you don't archive the files into a zip file or something similar, and secondly, ntfs for windows, which can not read ext3 without a third party utility.

---

