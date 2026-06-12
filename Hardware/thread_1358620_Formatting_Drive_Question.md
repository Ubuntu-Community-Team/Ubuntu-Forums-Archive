---
title: "Formatting Drive Question"
date: 2009-12-18
forum: Hardware
---

### Post by CarlosinFL on 2009-12-18
I am formatting a few drives and was told I should use fat32 since they're USB flash drives. My question is I don't see a mkfs.fat32 option but I do see the following:

```
mkfs          mkfs.bfs      mkfs.cramfs   mkfs.ext2     mkfs.ext3     mkfs.ext4     mkfs.ext4dev  mkfs.minix    mkfs.msdos    mkfs.vfat     

```

Can someone please tell me what the difference is between formatting a flash drive with 'msdos', 'vfat', or 'fat32' (which I don't even see)?

---

### Post by IcarusR on 2009-12-18
You need to use 'mkfs.vfat'

For details of 'mkfs.vfat' & 'mkfs.dos' see ```
man mkfs.vfat
```

---

