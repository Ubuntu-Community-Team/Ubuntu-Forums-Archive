---
title: "PLEASE HELP!! I Need to undo rm."
date: 2008-07-25
forum: General Help
---

### Post by mman426 on 2008-07-25
Hi, I just accidentally deleted a bunch of media files (music and videos) from a folder in /host (on my windows partition) and I really want to get them back. Is there any way I can do this. I am guessing the files wont be written over at least until I start up windows since Ubuntu shouldn't really be writing to that partition. Any help will be greatly appreciated.

---

### Post by tamoneya on 2008-07-25
you should use test disk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

The simplest way to get your hands on test disk is with a copy of the Recovery is possible liveCD: [http://www.tux.org/pub/people/kent-robotti/looplinux/rip/](http://www.tux.org/pub/people/kent-robotti/looplinux/rip/)

---

### Post by mman426 on 2008-07-25
Thank you, I hope this works, it would take a long time to download all that stuff again, plus I don't even know what was in there exactly.

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Testdisk is also available directly in hardy as a package.

I hear the program photorec (part of the testdisk package) works pretty well.

---

### Post by tamoneya on 2008-07-25
> **Yannick Le Saint kyncani said:**
> Testdisk is also available directly in hardy as a package.

I hear the program photorec (part of the testdisk package) works pretty well.

When doing recovery it is best to run from a liveCD.  That way you dont mount any partitions and possibly overwrite some of the deleted data.  Even though it is not in the / partition it is still a safe idea to not mount anything until you are making the attempt to read off the deleted data.  The first thing I typically do when I am working with data recovery is I clone my disk on to some sort of external or something.

---

### Post by Yannick Le Saint kyncani on 2008-07-25
> **tamoneya said:**
> When doing recovery it is best to run from a liveCD.  That way you dont mount any partitions and possibly overwrite some of the deleted data.

Hi tamoneya, oh I fully agree, this is not to recover anything from my main desktop, I have backups for that, many of them ... on multiple hard drives ... that I keep at different locations ... and I guard them with my life ;)

No, it's just to try it when someone will loose a hard drive / flash disk someday :)

---

