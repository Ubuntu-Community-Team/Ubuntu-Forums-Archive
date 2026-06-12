---
title: "How to marge disk partitions in ubuntu"
date: 2008-08-20
forum: General Help
---

### Post by Josep CA on 2008-08-20
Hi,
I'm a beginner using Linux Ubuntu and I would know if there is any easy way or program to merge two hard disk partitions. I want to merge a 65 GB disk partition with no data with another partition where I have Ubuntu installed.
I use ubunu 8.04 Hardy Heron.
Thanks in advance.

---

### Post by Elfy on 2008-08-20
You can use the gparted on the livecd - you need to delete the empty partition and then resize the ubuntu one to include the space. They need to be contiguous for it to be possible.

You will be working with partitions make sure you have backups of data in case of problems.

---

### Post by qstraza on 2008-08-20
gparted is very very usefull, when u will extend partition size, make sure that u have alot of time:p Or run it over night, it needs a lot of time, nothing wrong with that of course, at least that was my case...

---

### Post by Josep CA on 2008-08-20
Thank you.
I've installed GParted.
I've tried to delete the disk partition with no data (I've formatted it to ext3) but when I've tried to delete it I've got a message telling me the following:
"Please unmount any logical partitions having a number higher than 5".
I have no idea what unmount is. Can someone give me some help with it?
Thanks again.

---

### Post by Too Late on 2008-08-20
In gparted, you can unmount a partition by right-clicking it and select "unmount". However, if your root filesystem partition is one of those logical partitions, you cannot unmount it.

If you were using gparted LiveCD, there wouldn't be that problem (since nothing is mounted by default).

---

### Post by mgmiller on 2008-08-20
> If you were using gparted LiveCD, there wouldn't be that problem (since nothing is mounted by default).

This is correct.  You need to boot off a live CD to do this.  Go here and download the gparted live cd .iso and burn a live cd.  Then boot off it and away you go.

remember to back up first.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779/&abmode=1](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779/&abmode=1)

---

### Post by Elfy on 2008-08-20
If you trie dto do so from the buntu livecd you need to unmount swap first I think you can do so from a right click on the swap partition, or from a terminal

```
sudo swapoff -a
```

Or get a copy of gparted as mgmiller has said.

---

### Post by Josep CA on 2008-08-21
Hello again,
I've used GParted live cd to delete the hard disk partition and move the other one to its position. It seem to have worked.
However now when I try to turn on my laptop, after BIOS, a message is displayed.
The message is "GRUB loading, please wait... Error 22"
I can't run ubuntu and and the other operatic system I have installed (windows xp).
Thank you in advance.

---

### Post by timcredible on 2008-08-21
looks like you accidently wiped out your grub.  did you change anything to do with the first partition?  if not, then you can recover your grub with super grub disk (sgd).  the process is to download the sgd iso, burn it to disk, boot with that disk, then find your way through the maze of text menus to get to something that says something like 'fix grub'.  sgd works really well, but the menus aren't the easiest to figure out.

---

### Post by x1a4 on 2008-08-21
Hi,
You can use [FunionFS]("http://funionfs.apiou.org") which is a file system used to concatenate file systems together into one.  FunionFS is a user-space implementation.  If you prefer a kernel-space implementation (most likely what you're looking for) use [UnionFS]("http://www.filesystems.org/project-unionfs.html").

Both are in the repositories.

---

### Post by Josep CA on 2008-08-21
Hi,

> looks like you accidentally wiped out your grub. did you change anything to do with the first partition? if not, then you can recover your grub with super grub disk (sgd)

I dunno if hard disk partition I've deleted was the first partition. I'm a beginner in computers. I first installed win xp and later I installed Ubuntu in another disk partition. However, by mistake, I installed Ubuntu again in a third disk partition. I've been using this last disk partition and I've deleted the disk partition where I installed Ubuntu first (and his swap partition).
I've burned super_grub_disk_0.9745.iso and it seems it doesn't work.

> You can use FunionFS which is a file system used to concatenate file systems together into one. FunionFS is a user-space implementation. If you prefer a kernel-space implementation (most likely what you're looking for) use UnionFS.

Both are in the repositories.

How to use them when I only have access to my machine's BIOS?

Thanks

---

