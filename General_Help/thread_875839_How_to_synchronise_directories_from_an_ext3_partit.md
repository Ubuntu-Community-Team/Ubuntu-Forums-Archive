---
title: "How to synchronise directories from an ext3 partition to a FAT32 one ?"
date: 2008-07-31
forum: General Help
---

### Post by frodon on 2008-07-31
Hello,

I've been looking for a working solution for a long time now but haven't found any reliable one.

Let me explain, i have datas i want to sync on my desktop computers which are on a ext3 partition and i synch them on my external driver which is FAT32. Then on some occasions i want to synch datas from my external drive on my laptop drive which is ext3 and the invert.

Grsync and unison both generates problem with FAT32, because FAT32 can't keep permissions and seem to mess file creation dates therefore Grsync often want to overwrite the whole directories nullifying the interest of rsync.

Anyone found a way to bypath synchronization on FAT32 issue ?

---

### Post by justleen on 2008-07-31
you'll be stuck with the permission / date issue i guess..
how bout doing a find on both dirs, and do a diff on size/filenames?

---

### Post by frodon on 2008-07-31
yep that should work but since it is not sensible datas i would like something as simple as possible. But i agree with you that the "just live with it" way may be the best one.

But, hey, maybe someone found out a workaround we aren't aware of, lets hope :)

---

### Post by vanadium on 2008-07-31
In your scenario I would not hesitate and reformat the "external" driver to ext2 or ext3. This way, you will be able to synchronise without any problem. The grsync approach, which relies on rsync, indeed is a lightning fast way to mirror directory trees because only the changes are updated.

---

### Post by frodon on 2008-07-31
Unfortunatly this external hardrive is used by several people at home on MAC, windows and linux therefore FAT32 is a really the most convenient choice.

If there's no solution i think i'll just live with it, i synch these datas once a month maximum so i guess it is not worth bothering too much.

---

### Post by vanadium on 2008-07-31
Then you still might get away with it using the "--modify-window" option, which relaxes the comparison of the time stamp. This eliminates the problem preventing you currently to run quick updates.

For mirroring, instead of using the -a option (which stands for -rlptgoD) you might want to use the options -rlt only. See "man rsync" for details on what the options do.

---

### Post by frodon on 2008-07-31
Thanks for the tips, this may help i think, i will try this --modify-window option, i'm pretty sure rsync get lost only due file dates so this could definitely help.

I feel i'm near to solve my issue :)

EDIT: maybe --size-only option could help, never thought to use it.

---

### Post by justleen on 2008-07-31
doesnt the modified get mangled as well?

---

### Post by frodon on 2008-08-01
--size-only only option did the trick in my case even if i have still a bit more files to synchronize than i would normally need it's a way better result than before.
The --modify-window command alone was not enough efficient so since the datas i synchronize are mainly photos and videos --size-only option is just perfect.

Thanks all for your inputs, i was quite sure than an external view of this would help me and it did :)

---

