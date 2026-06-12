---
title: "How To Browse HD after Booting With Live CD"
date: 2005-01-03
forum: General Help
---

### Post by afonit on 2005-01-03
hello, 
I am having problems with my ubunto on the HD and it won't boot (it is a known issue [https://bugzilla.ubuntu.com/show_bug.cgi?id=496](https://bugzilla.ubuntu.com/show_bug.cgi?id=496) but not fixed yet)  

so I just need to get a few documents off of my HD.

I boot up on the live CD, but can't seem to browse the hard drive.
I did mount /dev/hdb1 (as root) and it mounted the drive on the desktop, all the files have 0kb's to them.  

how do you properly get to the HD from the live CD so that I can get at some of my files?

---

### Post by jdong on 2005-01-03
Sounds like corruption... Bad news.  You did mount the disk the correct way, but it seems like the data was somehow damaged.

Try running a fsck /dev/hdb1.

---

### Post by afonit on 2005-01-04
[QUOTE=jdong]Sounds like corruption... Bad news.  You did mount the disk the correct way, but it seems like the data was somehow damaged.

Try running a fsck /dev/hdb1.[/QUOTE]

well, the error I was getting when booting from the HD is:

starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel Panic - not syncing: Attempted to kill init!

---

### Post by afonit on 2005-01-04
when I do the fsck /dev/hdb1

I get

fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
/dev/hdb1:  recovering journal
/dev/hdb1:  clean, 175545/4947968 files, 2238258/9883810 blocks

---

