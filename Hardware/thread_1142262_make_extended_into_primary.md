---
title: "make extended into primary"
date: 2009-04-29
forum: Hardware
---

### Post by aeltester on 2009-04-29
Hey guys,

old situation:

winXP
mint5 root
mint5 home
mint6 all
logical {
    swap
    backup
}

step-in-between situation

winXP
logical {
    backuptoo
    mint6 all
    swap
    backup
}

I backed up backuptoo in order to get rid of it.

winXP
unallocated space
logical {
    mint6 all
    swap
    backup
}

my question is: how do I get this effing mint 6 partition to be primary again? It did become extended accidently at no data loss when I made the partition before it extended so it should be easy to get it back once the partition before is gone.

one more thing: it should be doable with linux *hatin M$*

hf
:P

---

### Post by ashgray2 on 2009-04-29
Try to use a Partition magic software. Run this software in your XP box. By using this software you can manage the partition you want to change.

---

### Post by aeltester on 2009-04-29
I tried it with norton but it wouldn't want to deal with the filesystems... well, I'll try once more...

thanks for the tip

---

### Post by aeltester on 2009-04-29
figured it out... thanks guys

hf
:P

---

