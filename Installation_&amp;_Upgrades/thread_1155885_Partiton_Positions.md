---
title: "Partiton Positions"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Splondir on 2009-05-11
Hello, I am going to create a new partiton table on my computer and then dual boot Ubuntu 9.04 and Windows 7. I want to have an ext4, swap, and ntfs partiton (no extended/logical partitons) on a 250 gb internal hard drive. I'm going to install Windows first so that I can use GRUB.

My question is, what order should these partitions be placed in? It probably doesn't matter, but I'm not sure, so I'm asking. Should I have the ext4 partiton first, the ntfs in the middle, and the swap at the end?

I also have one more unrelated question. I know there are Windows drivers to support reading ext2 which can be used to mount ext3 as ext2, can I do this with ext4?

Thanks in advance.

---

### Post by cholericfun on 2009-05-11
put the NTFS / windows partition first.


this is not always necessary but have a look here
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

under "Disadvantage of Installing Ubuntu after Windows"

i.e. the physical order of you partitions need not be the same as the numbering... BUT windows likes beeing on the first partition

---

