---
title: "Is it better to install Ubuntu without Wubi?"
date: 2008-09-17
forum: General Help
---

### Post by JKSnort on 2008-09-17
If you install Ubuntu with wubi does that run slower?

does this actually create a partition in the drive?

would it be better to create a partition and then install Ubuntu with a cd?

why?

---

### Post by pytheas22 on 2008-09-17
In principle, it's better to install Ubuntu using the traditional method, via the live CD.  One reason is that a system installed using wubi (the last time I checked) can't support hibernate.  The other reason is that when you use wubi, performance will be slower because the disk image that Ubuntu is installed to is part of an NTFS file system, so it's prone to fragmentation.  If it becomes fragmented, it takes longer to read and write from the disk.  In most cases, the slowdown is trivial, but if your Windows system is severely fragmented, performance under Ubuntu could be dramatically affected.

wubi doesn't create an Ubuntu partition, just a disk image inside Windows that Ubuntu gets installed to.

Of course, for many people the convenience of using wubi (easy, fast, no need to partition and easy to uninstall Linux later if necessary) outweighs the downsides, and in most cases there's no effectively serious difference between an Ubuntu system installed using wubi and one created with the live CD.

---

### Post by L815 on 2008-09-18
Say you have only 10gb partition for Wubi. If you decide to download everything to your larger partition, which would NTFS, if you try and boot the other OS which uses NTFS there will be BSOD (in Windows) if you try resume the same torrent.

---

### Post by 2damncommon on 2008-09-21
I have a number of Linux distributions installed to their own partitions.

I did a WUBI install of 8.04 to a Windows Vista partition. The WUBI install works as well as any other Version I have installed to it's own partition.

No doubt there are a number of reasons it is better to do a normal install to a Linux partition but a WUBI install works fine.

---

### Post by SunnyRabbiera on 2008-09-21
In some ways yes and other ways no.
Wubi is great to get one started though.

---

### Post by GoblinInventor on 2010-12-31
> In some ways yes and other ways no.
Wubi is great to get one started though. 

Strongly agree. Open source needs to get a wider audience, I mean it's not terribly difficult to install as it does most of the stuff for you, but lowering the bar to a windows executable is a lot less scary I think.

And less scary == good (at least in the beginning)

---

### Post by bcbc on 2010-12-31
If you choose Wubi, then just be aware that [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) will download release 10.04.1 by default. This can't be used to install netbook edition or Xubuntu. If you want 10.10 get it at [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

Do not update packages grub-pc or grub-commmon. They will stop wubi booting due to an outstanding bug.

Other than that it works just like the others say.

---

