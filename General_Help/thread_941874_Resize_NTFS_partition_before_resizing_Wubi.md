---
title: "Resize NTFS partition before resizing Wubi?"
date: 2008-10-08
forum: General Help
---

### Post by pjohnson on 2008-10-08
Hi, 

I've got Wubi installed to a second small NTFS partition ("D") but soon I'll need to resize the virtual disk because I'm running out of space. Before I can do that though, I need to resize that NTFS "D" partition because Wubi is already consuming the whole partition.

So my question is, what happens if I use PartitionMagic or something to resize "D"? Will I still be able to boot into Linux or will it completely mess up my MBR? 

After that I should just be able to use LVPM to resize the virtual disk right?

Thanks in advance.

---

### Post by ago on 2008-10-09
Should be ok. Also see the WubiGuide.

---

