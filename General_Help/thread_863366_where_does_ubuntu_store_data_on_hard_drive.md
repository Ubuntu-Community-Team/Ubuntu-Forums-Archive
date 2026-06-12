---
title: "where does ubuntu store data on hard drive?"
date: 2008-07-18
forum: General Help
---

### Post by harryliddic on 2008-07-18
where does ubuntu store data on the hard drive? At the beginning of the partition or toward the end of the disk. The reason I ask is that I am forced to use either a windows or linux video editing program and I need more disk space to hold a 28G file. I have to give a haircut to either windows or linux on my dual boot with fdisk(correct me if I am wrong on using fdisk). I don't want to lose any data from either side but I need to move the partition on way or the other. Which is best?

---

### Post by Het Irv on 2008-07-18
I belive I stores it at the beginning of the disk, but I am not sure. 
Here is the link to the Wiki for ext3, the filesystem that Ubuntu uses.
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

---

### Post by jimv on 2008-07-18
It's irrelevant.  Any decent partition editor will be able to resize or move a partition without losing the data inside.

And btw, I would use a Gparted boot disk to do this.  Much more reliable than fdisk, and the GUI interface is much preferable to text.  You can download the ISO here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Just burn that to a CD and boot up from it.

Gparted also will show you how much space is used on each partition, so you'll be able to see how much space you can free up.

---

### Post by damis648 on 2008-07-18
> **jimv said:**
> It's irrelevant.  Any decent partition editor will be able to resize or move a partition without losing the data inside.

Completely. Use gparted on the LiveCD or try the Parted Magic LiveCD. They'll do it all for you.

---

### Post by jimv on 2008-07-18
> **damis648 said:**
> Completely. Use gparted on the LiveCD or try the Parted Magic LiveCD. They'll do it all for you.

For some reason the version of Gparted on the Ubuntu live cd kept erroring out on me yesterday when I was moving my Ubuntu partition (after deleting the XP partition, hurray!).  The version on the Gparted Boot CD worked ok though.

---

