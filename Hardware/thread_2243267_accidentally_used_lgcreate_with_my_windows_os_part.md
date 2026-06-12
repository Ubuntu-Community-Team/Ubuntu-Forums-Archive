---
title: "accidentally used lgcreate with my windows os partition, now it wont mount"
date: 2014-09-07
forum: Hardware
---

### Post by cazper2007 on 2014-09-07
hi all,
so as stated above, i accidentally used lgcreate with my windows os partition, now it wont mount and says ntfs error. restarted and tried to boot windows, didnt work. now linux sees the drive as lvm instead of ntfs. any way to fix this without reformatting my drive, and if not, is there any way to recover my files from this drive (if theyre not already gone)?

---

### Post by weatherman2 on 2014-09-07
The partition is gone; you're going to have to re-install Windows.

You can probably recover most of your files before that, though - but don't do ANYTHING on that disk until you do!  Don't try changing/adding/deleting partitions.  Leave it alone until recovery is complete.

There are lots of free recovery programs - do some googling.  Depending on what you are trying to recover, you may have better luck connecting this disk to a working Windows installation and using Windows recovery software, but there are free Linux versions as well.  (e.g. testdisk.)  The Parted Magic distro (still a free one available from last year I think on MajorGeeks) has some built-in recovery tools like testdisk I think.

You may even try using TestDisk to recover the NTFS partition - but don't hold your breath:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Mark Phelps on 2014-09-08
The only free Windows data recovery app I know of is Recuva.  You will need to connect your drive to a PC running Windows to install and use that.

If Recuva doesn't find what you want, you should try RecoverMyFiles.  It's free to download, install, and try -- but you have to buy a license to do actual file recovery.

---

