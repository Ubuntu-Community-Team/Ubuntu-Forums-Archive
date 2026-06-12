---
title: "wubi on second partition windows xp"
date: 2008-08-05
forum: General Help
---

### Post by RJQ on 2008-08-05
I have a hd with two partitions on it, the first one allocates the recovery system and the second one has the windows xp os, I realize that wubi will place some files on the first partition and the grub (used for my entire bunch of os'ses) is not capable to start the wubi/windows menu. Does any one knows if there is a way to prevent this files to be installed on the first partition? or a workaround once they were wroten there?
thanks in advance

---

### Post by Qchan on 2008-08-05
> **RJQ said:**
> I have a hd with two partitions on it, the first one allocates the recovery system and the second one has the windows xp os, I realize that wubi will place some files on the first partition and the grub (used for my entire bunch of os'ses) is not capable to start the wubi/windows menu. Does any one knows if there is a way to prevent this files to be installed on the first partition? or a workaround once they were wroten there?
thanks in advance

[b][color=darkred]
Wubi installs inside of an image file. It doesn't mess with any partition you have. For it to boot, it uses the boot.ini located in C:\. This implements an option to boot Ubuntu through NTFS via the image file its installed in.

So, to make it simple. Wubi doesn't see any partition on your computer. It just installs itself inside of an image file.
[/b][/color]

---

### Post by RJQ on 2008-08-06
Well somehow wubi place this two files in the first partition *wubildr, wubildr.mbr*, another set of the same are in c:/ and also inside the folder named ubuntu, but now I am almost sure the reason way grub does not boot it is because I am using gfx instead of the original grub. still bootlable with the super grub cd...

---

