---
title: "Ubuntu installed twice"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by The Wagster on 2009-07-12
Hi, I'm new to linux and thought I'd give ubuntu a try dual booting with XP.  But I had a bit of trouble with the install and partitioning and now have Ubuntu installed twice on my PC - it's like a tri-boot system!  How can I remove one of the installations?

My hard drive was already partitioned from the XP install and had a nice 180Gb drive that I had never used, the idea was to install Ubuntu 9.04 there.  When I went through the install I got to the partitioning bit and left the install to do it's own thing, thinking it would recognise that area and install itself there.  Instead it added another partition of only about 3Gb and installed Ubuntu there.  Sadly this area is far too small.

Reading about how to change the partition I learned the install disc has a partition resizer, GParted, on it so I wacked the install CD in and rebooted... thinking it would allow me to change the existing install but actually it went through a full install!  At least this time I gave it a decent partition.

So now I have two installations on my PC, one in a decent size partition and the other pretty much useless.  How can I uninstall just that one instance of Ubuntu and re-partition that 3Gb back into one of the main partitions?

Thanks for your help.

Wag.

---

### Post by Partyboi2 on 2009-07-12
Hi, you can use gparted, boot the ubuntu live cd to the Desktop then go to System>Admin>Partition Editor and delete the ubuntu install you don't want and use the resize option to increase the size of the one you want to keep.

---

### Post by The Wagster on 2009-07-12
Thanks!  I got a Grub error after re-partitioning but managed to fix that.  Working perfectly now!

Cheers.

---

