---
title: "Best way to install when I have multiple drives"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by niw_uk1964 on 2009-11-01
It's a 64 bit install I will be doing, but relevant to all installs, hence why I am posting here.

I have 6 drives in my system.

1. 750GB SATA
2. 1.5TB SATA
3. 1.5TB SATA
4. 1.5TB SATA
5. 750GB SATA
6. 160GB PATA

I want to install on 1, so I was going for it as follows:

1.
120GB mount point /boot
430GB mount point /home

I want to put a 30GB swap partition on 6 with the remaining 130GB for temporary storage and general rubbish on there.

The remaining drives I will use them for data and virtual machines.
I would like to put the VMs on one drive - probably the other 750GB drive and they would then share the data on the other drives.

How's the best way of going about it? What mount points do I use?


TIA.

---

### Post by dabang on 2009-11-01
That's a lot of disk space! ;-)
I don't know about your /home, but giving /boot 120GB is a little too much. 120MB will be enough (or make it 500MB, to be on the safe side and install a few more kernels). Within /boot resides the kernel and grub configs only. With one kernel installed, my /boot takes about 50MB.

---

### Post by niw_uk1964 on 2009-11-02
Yep...that's some space...my Windows Server (yeah, yeah...I know) has 9TB of it.

Anyway, thanks for replying...noted. But I am still not clear as to the best way to mount the other drives as the installer gives a number of options such a /, boot, usr/local etc.

---

### Post by dabang on 2009-11-04
As disk space doesn't matter:
swap: twice the size of RAM
/boot: 512 MB
/var: 15 GB
/: 30 GB
/home: feel free
Mount all other disks/partitions under /media/<some dir>, you can leave your VM images there

But it really depends on usage and personal preferences...

---

