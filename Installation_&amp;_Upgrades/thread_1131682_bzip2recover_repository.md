---
title: "bzip2recover repository?"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by TDFlanders on 2009-04-21
Hi there,

I created an archive through file-roller, but found it got corrupted. This is my error message:

An error occurred while loading the archive.

(null)

> Command line output

bzip2: Compressed file ends unexpectedly;
    perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

This does not seem to be in main, proposed, multiverse or anything.

I tried to sudo apt-get install bzip2recover, gnome-app-install, synaptic, ...

I also just f*****g googled it already.

Any tips?

Tx,

Thomas

---

### Post by Anthon on 2009-04-21
Are you sure this is a bzip file? Try
  file filename
I thought the file-roller would create zip files not bzip2 files.

---

### Post by TDFlanders on 2009-04-21
No, file-roller is just the frontend for Archive Manager, so it does not default to zip files. I think 7zip and rar need to be installed seperately. bzip2 and .tar.bz2 formats are standard, with .tar.bz2 being the default. Thanks for the effort though, no ideas where to find bzip2recover? Thanks again,

Thomas

---

### Post by Anthon on 2009-04-21
bzip2recover is part of the  bzip2 package on my 8.10 system:
  dpkg -S $(which bzip2recover)
generates a output
  bzip2: /bin/bzip2recover

---

### Post by TDFlanders on 2009-04-26
Thanks a lot for that Anton,

bzip2recover was indeed installed on my system.

I did not find an entry for:

$ bzip2recover --help
<NOR>
$ man bzip2recover

This had me confused.

Thanks again,

Thomas

---

