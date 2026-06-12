---
title: "Can you fix my banged up hard drive?"
date: 2008-08-09
forum: General Help
---

### Post by Paqman on 2008-08-09
I've got a laptop that took a bit of a whack, and has been none too happy since. 

I've booted up into a LiveCD and run an fsck with the following results:

```

ubuntu@ubuntu:~$ sudo e2fsck -f -p -v /dev/sda5
Error reading block 1341321 (Attempt to read block from filesystem resulted in short read) while reading indirect blocks of inode 651594.  

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

```

So I did:
```

ubuntu@ubuntu:~$ sudo e2fsck -f -v /dev/sda5
e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes
/dev/sda5: e2fsck canceled.

/dev/sda5: ********** WARNING: Filesystem still has errors **********

```

Now, I don't really know what i'm doing here, and the e2fsck man page doesn't seem show an obvious way forward.

Clearly this partiton has suffered some damage. Is it curtains, or can I somehow repair the filesystem around the damaged blocks?

---

