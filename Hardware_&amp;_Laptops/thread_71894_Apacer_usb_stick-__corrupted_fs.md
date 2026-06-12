---
title: "Apacer usb stick-  corrupted fs"
date: 2005-10-04
forum: Hardware &amp; Laptops
---

### Post by stoeptegel on 2005-10-04
I had some compatible issues between winxp and kubuntu: files who didn't appear to be readable from one another and  ended as 0kb filesize.

Today i spotted some files being renamed by itself with a ~ in it, so i started to look into this, and did a look on the properties of the directory  'trash-~1' which appears to have a endless loop of directories. :(

This is why i came to the dessision to backup and remove all files form the usb stick, but some file didn't agree with me on that so i switched to konsole:

```
$ rm -rf trash-~1
rm: WARNING: Circular directory structure.
This almost certainly means that you have a corrupted file system.
NOTIFY YOUR SYSTEM MANAGER.
The following directory is part of the cycle:
  `trash-~1/info/trash-~1/info'
```

My question:
Are there any known incompatible issues between files made on winxp vs. linux as far as usb stick goes, and how do i cure this 'apacer handy steno' baby?

---

### Post by mlomker on 2005-10-04
>  linux as far as usb stick goes, and how do i cure this 'apacer handy steno' baby?

If it is an empty stick then why not just reformat it?

```

sudo mkfs.vfat /dev/sdX

```

---

### Post by stoeptegel on 2005-10-04
Good point.
I did the format (at blazing fast speed (?)), and it's working now.

Thanks mlomker, i couldn't make it one week without you guys...

---

### Post by mrgod on 2007-06-19
Does anyone know how to fix this without formating?
I've tried to delete the folders, but it would'nt do ut..

---

