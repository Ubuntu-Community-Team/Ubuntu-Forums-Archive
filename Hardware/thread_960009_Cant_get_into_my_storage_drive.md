---
title: "Cant get into my storage drive"
date: 2008-10-27
forum: Hardware
---

### Post by Greensystemsgo on 2008-10-27
my ntfs drive with all my music, and videos and past projects is inaccessible via linux, and im not quite ready to reinstall windows, however im close, im very frustrated.  Also um running 8.04 lts x64 with all the latest updates. Also, this drive has never had windows installed on it, it served as my backup drive, however who knows what vista has done to it.

I receive numerous errors whilst attempting to mount my secondary drive, named New Volume, or as linux knows it, sdb, or with its only and single partition sdb1

when i mount i either A)receive instructions on how to do it [which obviously dont work or i wouldn't be here], or B) it says i don't have permission [to access MY own hard drive that i bought and paid for?].

So i went ahead and added a line to my /etc/fstab file, it reads like follows,

/dev/sdb1/media/New Volume_ ntfs-3g force 0 0

And that doesn't work either, even after restarts and what not. So if anyone has a cure, please help!

---

