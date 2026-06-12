---
title: "Removing Ubuntu"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by ChakaZulu on 2009-02-21
I have a Compaq laptop with Windows Vista. I finally managed to get Ubuntu 8.04 installed by using the text mode. Vista will still boot up just fine but Ubuntu hangs for a while then I get an ALERT! and it goes to busybox and (initramfs). I tried removing the splash screen and that doesn't help. I can't find a solution to this so I just want to get this off of my system! How can I now get rid of this wasted space? Is it possible to somehow uninstall even if it won't fully load?

---

### Post by Mark Phelps on 2009-02-21
Did you install inside Vista (using Wubi) or did you create another partition and install using dual-boot?  Answer depends on which you did.

---

### Post by ChakaZulu on 2009-02-21
I installed in a separate partition so I could duel boot. I wish it would just load then I wouldn't have to worry about it.

---

### Post by ve4cib on 2009-02-21
If you installed Ubuntu on a separate partition then you should be able to boot into Vista and reformat the partition.  That should nuke it pretty well I should think.

That is a very weird error though.  I've never, ever seen it (or even heard of it) and I've been using Ubuntu for years.

---

### Post by ChakaZulu on 2009-02-21
Ok I will try that. Yeah when I edit in grub and take the splash screen off I can see all of the text as it starts to load up but then it does some kind of exit and I get this:

check root=bootarg cat /proc/cmdline
or missing modules, devices:cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/e34(bunch of numbers here) does not exist. Dropping to shell!

Busybox...etc....

(initramfs)

---

### Post by ChakaZulu on 2009-02-21
This is the whole error:

udevd-event[1483:] run_program: '/sbin/modprobe' abnormal exit
^@Done.              < it gets to this point quickly then sits here for a while...says "Done" then the next part>

check root=bootarg cat /proc/cmdline
or missing modules, devices:cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/e34(bunch of numbers here) does not exist. Dropping to shell!

Busybox...etc....

(initramfs)

---

### Post by fudoki on 2009-02-21
Sounds like the Ubuntu install did not successfully complete.  Just install Ubuntu again, being sure you format the Linux partition using ext3 or reiserfs, watch the messages and make sure the Ubuntu install successfully completes.

Microsoft added some "functionality" to Vista to attempt to block the installation of any other operating system on the drive, but like all M$ software, it doesn't fully work, but can foul the first install attempt.  Installing again usually works.

The best thing to do is buy a SATA 2, 16Mb, 7200RPM, 250Gb drive for $45, slap it on there, make a / and /home partition and install Linux there.  Then format the partition on the Vista drive using FAT32 (note the Microsoft 64Gb limitation, may need to make 2 or so partitions) and you will be able to access that space from either OS.  The Linux support for Vista's flavour of NTFS is not yet 100% (again, M$ deliberately trying to thwart the use of Linux), so the FAT32 strategy makes it easy to share data with confidence.

Hope this helps.

---

### Post by ChakaZulu on 2009-02-23
Thank you for your suggestions, I tried to reinstall it and it installs correctly but then when trying to boot it up, the same thing happens. I think I'll just delete it and in the future, get an external hard drive and load it there.

---

