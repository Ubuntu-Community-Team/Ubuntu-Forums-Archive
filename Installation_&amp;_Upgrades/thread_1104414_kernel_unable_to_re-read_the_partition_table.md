---
title: "kernel unable to re-read the partition table"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by HomerSimpson748 on 2009-03-23
I'm trying to set up a software raid using the 8.04.2 server installer.

After setting up the partitions and writing changes to the disks I get the error "The kernel was unable to re-read the partition table on /dev/md/1 (invalid argument). This means linux wont know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/md/1.".

I've been trying to get this figured out all day long. I've done this a dozen times before and never had a problem. Any thoughts?

---

### Post by HomerSimpson748 on 2009-03-23
Well, I've looked into it a bit more and found it's an old bug that has worked its way back in...

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/305500/]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/305500/")

A bit disappointing.

---

