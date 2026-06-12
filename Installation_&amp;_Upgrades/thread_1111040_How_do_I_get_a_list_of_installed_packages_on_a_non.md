---
title: "How do I get a list of installed packages on a non-root disk?"
date: 2009-03-30
forum: Installation &amp; Upgrades
---

### Post by keris on 2009-03-30
I have an Ubuntu 8.04 (Hardy) system which has crashed, the root disk is no longer bootable or even readable -- but its backup (a straight file-by-file (over rsync) copy) is readable (but not bootable).  How can I get from that a list of which packages were installed?

I know that I can get a list of installed packages on a running system using dpkg -l | grep ^ii, but in this case I suspect that what I need is the file/directory underlying that data.  Or a way to point dpkg at the data on the other disk.  If it is in text format (and an old memory from early Debian days suggests that it may be) I can then run it through a Perl script to turn it into apt-get commands for the rebuilt system to get it to the same (or equivalent) state.

Thanks for any pointers...

---

### Post by lemming465 on 2009-03-31
I'd try **dpkg --admindir=*/mount/path/to/var/lib/dpkg* --get-selections**

---

### Post by keris on 2009-04-06
> **lemming465 said:**
> I'd try **dpkg --admindir=*/mount/path/to/var/lib/dpkg* --get-selections**

Thanks.  It was particularly the location (/var/lib/dpkg) which I hadn't found, and the --get-selections (and its reverse --set-selections) which I suspect I never knew.  List of packages now extracted and in a safe place waiting until I get a new motherboard and disk to rebuild the machine...

---

