---
title: "Can't see my cd drives?"
date: 2009-05-20
forum: Hardware
---

### Post by MadEric on 2009-05-20
Very new to Ubuntu! Have recently installed Ubuntu 9.04 but can't see my cd drives. Just get Floppy drive & File system when looking in Computer. Looked in dev but can't find anything related to cd drive!

fstab as follows:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Looking at the fstab i assumed i'd find scd0 in dev, but it's not there. Can anyone give me some very simple instructions on how to resolve this. 

I've also tried sudo mount /dev/scd0 /media/cd but this fails as can't find scd0.

Thanks
Eric...:o

---

