---
title: "Second Harddrive NTFS not mounting"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by khaledaboualfa on 2006-10-31
Hello all, just installed Edgy onto the main harddrive, with Ext3 file system. I have a second harddive which used to be on windows and therefore an ntfs system. This second harddive is where all of my files and data are. When I type in:

```
sudo fdisk -l
``` 

I get the following output (currently I'm also trying to sort out my external modem so this isn't an exact screen dump, I can put any more information you need):

```
Disk /dev/hdd: 200.0 GB

Device     Boot   Start   End   Blocks         ID    System
/dev/hdd1    *     1      24320  195350368+    42      sfs
/dev/hdd2         24321    24321   8032+       42      sfs
```

Then when I try and edit my fstab file and put ntfs (OR SFS even) I get the following error message:

```
wrong fs type , bad option, bad superblock, on /dev/hdd, missing codepage or other error
```

Any ideas how to go forward with this, and actually mount the harddrive?

---

