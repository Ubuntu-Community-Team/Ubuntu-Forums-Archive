---
title: "is it possible to install to a 5000 MB ntfs partition?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by tay on 2005-12-23
that i have setup as C: and my windows xp partition is on D:
i would like to install breezy 5.10 on this partition. can anyone clearly explain in as little words as possible how to burn an iso image from xp onto this partition and then boot install from this partition successfully.  also does anybody have any reccomendations for a good 3rd party boot manager?

---

### Post by fordfan753 on 2005-12-23
It's not possible to install any linux on NTFS partitions.

---

### Post by fordfan753 on 2005-12-23
However, what you can do is use the partitioner that comes with ubuntu, and make it use that partition, it will format it to a format you specify (I like reiserfs, but ext3 is ok) you'll lose anything on that partition, but you'll get ubuntu on it...

As for boot managers, I think 99% of people on the forum would recommend GRUB, it's pretty hard to beat, and can boot almost anything.

---

### Post by tay on 2005-12-23
why do you say reiserfs ?

do you think 5000 MB is enough for breezy after updates and everything?

i read a couple threads before about people having problems with grub and xp.

---

### Post by darth_vector on 2005-12-23
reiserfs is super fast for handling lots of small files and it never, ever fragments. ext3 can fragment a little bit, but not very much.

i would think that 5GB is more than adequate, provided you dont expect to download dvd images and play large games.

i have grub and xp and never had a problem. some people do, most people dont. even if you do have problems, they are fixable.

---

