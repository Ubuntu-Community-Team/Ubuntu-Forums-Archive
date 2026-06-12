---
title: "hard disks errors?"
date: 2012-05-06
forum: Hardware
---

### Post by lo.j on 2012-05-06
hi all.

i execute smartctl weekly on all my disks and it has never reported anything wrong.

today i was playing with e2label and i got:```
e2label: Bad magic number in super-block while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

e2label: Filesystem revision too high while trying to open /dev/sdd1
Couldn't find valid filesystem superblock.
```

extra info: sdc and sdd are part of a raid5 array.

i thought that smatctl was reliable enough, isn't it?
how can i investigate further?

thanks.

---

### Post by lo.j on 2012-05-07
just looking for any opinion and suggestion, mostly to fit raid management and disk health...

---

### Post by lo.j on 2012-05-07
ok, i got this.
being single raid members, it doesn't make sense to label "a part" of a logical volume.

the strange thing is that e2label does not return any error if used on the first volume (rather it returns the array label!), while it raises two different errors for the other two. [-(

---

