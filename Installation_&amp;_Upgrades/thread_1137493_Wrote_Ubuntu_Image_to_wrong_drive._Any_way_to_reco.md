---
title: "Wrote Ubuntu Image to wrong drive. Any way to recover data?"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Palal on 2009-04-25
Upgraded my main laptop to 9.04 yesterday without too many problems. Went to upgrade my EEE PC this morning. Downloaded the image and started writing to a drive.

The problem is I wrote to my 750GB external drive, not to the 1GB flash drive. (I have backups of most data on another drive, so most of it isn't a problem).
:lolflag:

To complicate matters, that partition was NTFS.

Any way to recover the data?

---

### Post by DracoJesi on 2009-04-25
[http://ntfsundelete.com/]("http://ntfsundelete.com/")

[http://www.recuva.com/download]("http://www.recuva.com/download")

and for linux

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

[http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

---

### Post by Palal on 2009-04-25
So one of the problems is that the partition table was deleted, so these windows utils are of no use. Trying PhotoRec to see what I can recover. Thanks.

---

### Post by DracoJesi on 2009-04-25
ah, see I was wondering about that, I didn't know if you had installed Linux before since you were using a NTFS file system on the external enclosure, didn't know what OS, I got two for each just in case :)

---

### Post by Palal on 2009-04-27
I actually have both Ubuntu and Windoze installed... although I use ubuntu 99% of the time these days.

Problem solved. Used "R-Studio" (Windows) to recover files from the lost partition.

---

