---
title: "Reiserfs boot problem:  Bad block  5849"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by frazelle09 on 2007-11-27
i've got two partitions hda1 and hda2.  The first has the OS and the second had /home.  When i boot now, reiserfs reports a bad block and will go no further, suggesting i use the -B option for fsck.reiser .  When i try this

fsck.reiser --rebuild-tree

i get a very scary message about not using this option if i'm having problems accessing some sectors -- Huh?  Well, at least they're kind enough to warn us.

Am i trying the correct proceedure to fix this?  What else might i try to get this to correct this bad block so we can at least boot and copy the two partitions onto another hd?

If i run the LiveCD, it sees both partitions just fine and i can access files on them, also just fine so i suppose that all is not lost... yet.

Could i just use partimage on each partition, copy the files to a CD? or DVD or another HD and then use partimage again to load them on a newly formatted, new HD?

Thanks for any help and have a great evening!  :)

---

### Post by napsy on 2008-02-25
I can confirm this bug using hardy alpha on a fujitsu-siemens laptop. Using the fsck --rebuild-tree will recover files from the partition but some names of the directories will be lost.

---

