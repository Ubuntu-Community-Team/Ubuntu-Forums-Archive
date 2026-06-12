---
title: "gateway t2862 having serious problems..."
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by mason_feduccia on 2007-12-24
alright...so i have this brand new gateway laptop that i really wanted to put ubuntu on....but the laptop had vista preinstalled and i figured that would cause problems, so i decided to set up a dual boot...everything went fine...
then i did something really stupid and just deleted the partition that was set up for linux....

now i cant even boot my system...all i get is a black screen with something like this:

   GRUB loading stage1.5

  GRUB loading, please wait...
  error 22

i have no idea what to do!!!!!!
is there anyone out there with any advice?

---

### Post by lkraemer on 2007-12-26
I'd think the best thing would be get online with another computer and download
SUPERGRUB.  Make a floppy, then repair the Boot problem, (so it boots windows and
not the GRUB menu, then just reinstall Ubuntu.)  Easy and it works fine, it just takes
a bit of reading on Supergrub.

When Supergrub has repaired the problem............
While you're at it why not just boot the Ubuntu 7.10 LiveCD and run Gnome Partition
editor to create three partitions:
\                 ~10-20Gig
\home         ~remaining drive space
\swap          ~8 Gig

Then Install Ubuntu, and MANAGE the partitions, and edit the mount points to be as
noted above.  This will allow you to wipe the \ Partition, and your data in \home
should be safe.

LK

---

