---
title: "Cannot open my windows partition..."
date: 2008-12-22
forum: Hardware
---

### Post by Matisoft on 2008-12-22
Hi, I'm new here and I have a problem with my HD.

I have two partitions, windows and ubuntu in my HD.
When I have been working in windows (one week ago), I was unmounted a pendrive, but not safely correct (because windows crashes!).
Now, I can't open windows because it stays on a black screen for all time...

I'm trying to mount the windows partition on ubuntu, to recover all files, making this...

sudo ntfsmount /dev/sda2 /media/sda2 -o umask=0,force

I can mount the partition but I can't access it (the filesystem seems to be corrupted...) I can view the files (with ntfsls) and that says that my files are intact, but I can't access it.

I cannot make chkdsk or also equivalent on windows because I can't open windows! And also I can't use a recover CD or install CD because when it detects the HD, it stops and put the black screen again...

How can I open my windows partition?

Thanks

---

### Post by SlidingHorn on 2008-12-22
See if this helps at all: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Matisoft on 2008-12-22
Thanks! I'm using TestDisk to view the files on the partion.
I'm lucky because I don't have a lot of files to save... but the problem stills unsolved by other users that can have the same problem..

How can we fix the unsafely extraction problem on windows? It's necessary to format de HD?

---

