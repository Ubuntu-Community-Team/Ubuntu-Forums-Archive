---
title: "tar &amp; un tar Data integrity error"
date: 2008-08-12
forum: General Help
---

### Post by shadowhywind on 2008-08-12
Hi all, having a bit of a problem. I am trying to make a backup of my linux partition, using the command ```
sudo tar -cvjf disk-1/backup.tar.bz2 -C rootfs . 
``` which runs exactly what I want, and leaves me a 6 gb tar.bz2 file. However the issue i get is when i un tar the file using```
tar -jxvf backup.tar.bz2
```  I will randomly get this error.
```
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```

I reran this command two more times, it happened in the same spot as the first time, and then the third time the error happened in a different spot. I even deleted the tar.bz2 and started from the beginning and still i have this issue. I am thinking that perhaps it has an issue being 6 gb? any ideas. thanks

---

