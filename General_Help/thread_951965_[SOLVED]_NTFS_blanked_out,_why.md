---
title: "[SOLVED] NTFS blanked out, why??"
date: 2008-10-18
forum: General Help
---

### Post by Monotoko on 2008-10-18
hiya guys, i just tried to format my second partition, which isnt mounted, into an NTFS partition so that i could install windows to it.

Now, the problem im having, is that whenever i try to do this, ntfs is blanked out, the only ones i can format it to are: FAT16, FAT32, Ext2, Ext3, linuxswap and reiserfs, the rest are blanked out, could anyone explain why this is?

---

### Post by Yellow Pasque on 2008-10-18
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
```
sudo apt-get install ntfsprogs
```

---

### Post by Monotoko on 2008-10-18
Thank you! just what i needed :)

---

