---
title: "Is NTFS completely writable now without risks ?"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by GAJ on 2006-01-15
Hello all,

I would like to know if - despite the (yes|no?) up to date documention - the NTFS partitions are now writable from Breezy Badger (Ubuntu 5.10, updated 2.6.12 kernel ) ?

In other words, is it possible to use the NTFS partitions as readable and writable backup partition from within the Linux desktop without the risk to lose data ?

Thank you for your knowledge and all your feedback,

---

### Post by bobyang on 2006-01-15
that's not a good idea.
yes, kernel 2.6 supports read/write NTFS partitions, but maybe you will get problem for reading NTFS partition in windows after you writed it in linux, not all the time, but sometimes.

---

### Post by aysiu on 2006-01-15
It's not 100% safe yet. If you must, create a separate FAT32 partition for sharing files.

---

### Post by Mr_Grieves on 2006-01-15
Read about writing to NTFS in Linux here:
[http://www.linux-ntfs.org](http://www.linux-ntfs.org)

People are working on it.. and there is a solution out there. I haven't tested it myself.

---

### Post by Adrian on 2006-01-15
[QUOTE=aysiu]It's not 100% safe yet. If you must, create a separate FAT32 partition for sharing files.[/QUOTE]

Or share an ext2/ext3 partion:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

That works fine for me. The FAT solution is easier however, and I recommend it instead if you don't want to share a large amount of data (on large partitions).

---

### Post by GAJ on 2006-01-16
Ok folks, thank you very much for the feedback. As I can see for now, I have to wait a little bit to use this safely... Ok.

My best,

---

### Post by frodon on 2006-01-16
Maybe but remember that NTFS also don't support unix rights and ownership, it's something which really annoy me with NTFS and FAT32 and it's why it will never be a good FS for linux.

---

### Post by lutosdemayo on 2006-01-16
If you must share files on the your windows get explore2fs. Write it in linux read it in windows.

[http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

---

