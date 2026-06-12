---
title: "Fsck time worries."
date: 2008-10-30
forum: General Help
---

### Post by pdaggitt on 2008-10-30
Hey, I have a question for everyone. How long should fsck take to run on a 750gb ext2 (sata) disk? I have a feeling i am not gonna like the answer.

---

### Post by tubezninja on 2008-10-30
It's not so much the capacity of the hard drive as it is how MUCH of the hard drive's capacity is utilized.  If you don't have a lot of files or directories and the drive is relatively empty, then fsck should be pretty short.  

If you have lots of files or a complex directory structure, it's going to take a while.  Like an afternoon, maybe. :)

---

