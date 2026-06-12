---
title: "Ubuntu 11.04 Not recognizing Floppy Drive"
date: 2011-11-23
forum: Hardware
---

### Post by Hugojax on 2011-11-23
Friend of mine is having this issue. The fd0 file is not in the /dev folder. Tried the lshw - C disk command and it doesnt show the drive. Any help would b appreciated.

---

### Post by An Sanct on 2011-11-23
Did you mount the floppy? :)

Insert the media and mount it.
```
udisks --mount /dev/fd0
```

PS. I know people, that don't even know, that commonly, there where two types (sizes) of floppies... Well, my point is, that it surprises me, that floppies are even supported at the moment... can't remember the last time I used one :) (My C64 is excluded from this ;))

---

### Post by gordintoronto on 2011-11-24
Just to add to what An Sanct said, you won't ever see the floppy unless it has a diskette in it.

I have read that you need to unmount it before removing the diskette, because there might be unwritten data.

---

### Post by An Sanct on 2011-11-24
yap :) unmounting USB drives could be _drastically_ different than unmounting something like a floppy ... I deferentially have to agree with *gordintoronto* as it is deprecated hardware.

Take good care of your floppies!

---

