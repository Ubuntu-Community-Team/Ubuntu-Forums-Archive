---
title: "[SOLVED] Error  copying files from Ubuntu to Windows or OS X"
date: 2008-11-24
forum: General Help
---

### Post by whatever69 on 2008-11-24
Hi,

I'm copying some large files (700MB to 1.4GB) from my Ubuntu machine using mapped drive to my windows XP (Using Samba).  Certain files copy fine, but some consistently give me the following error:

> "error copying file or folder the request could not be performed because of an I/O device error"

I tried copying to my local disk and to a USB disk to no avail.  The same files always produce the same error.

So then I tried from my macbook with the same file from Ubuntu (mounted as NFS) and I got the following message:
> 
"The Finder cannot complete the operation because some data in "foo.avi" could not be read or written. (Error code -36).

The permissions on the file are fine.  I have admin rights on all machines.  Have I accidentally damaged several files?  How did I do this?  Or rather, what is going on here?

Just want to add that my file system is 4 HDs in RAID5.  Running:

> sudo mdadm --detail /dev/md0

shows that everything is clean. Is there any other tools I can use?

---

### Post by whatever69 on 2008-11-26
SOLVED:

I learned the hard way by the way never to run fsck on a mounted volume.  I did on my OS volume and it booted me to "safe" mode where it mounted the '/' volume in readonly.  It ran fsck on it again and it fixed the OS.  However, the original problem was that my raid file system had some corrupted files.  I first unmounted the file system:

```
$sudo umount /dev/md0
```

Then I ran fsck with the -y options which answers yes to all questions.

```
$sudo fsck -y /dev/md0
```

It ran for a couple of hours seeing as I had about 600 GB of total and data and now it's fixed!

Btw, I figured this out when I got the message that the volume /dev/md0 had been mounted 442 times without a check.

---

