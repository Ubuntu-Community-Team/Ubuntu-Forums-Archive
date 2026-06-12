---
title: "error while formatting usb flash drive"
date: 2010-01-25
forum: Hardware
---

### Post by repsakkgn on 2010-01-25
i tried to format 2 different flash-drives and all i get is 
error creating file system: helper exited with exit code 1: helper failed with:
Total number of sectors (2005120) not a multiple of sectors per track (62)!
Add mtools_skip_check=1 to your .mtoolsrc file to skip this test

is it normal? what's the solution? please help!!

---

### Post by linux nut on 2010-01-25
What program are u formatting the usb and what file are u trying to format it with?

---

### Post by repsakkgn on 2010-01-25
i just do right click on flash drive icon on the desktop then choose format and then filesystem fat32...tried ntfs - same result.

---

### Post by linux nut on 2010-01-25
If ur doing it on windows then did u change all the setting you needed to.

---

### Post by repsakkgn on 2010-01-25
why windows? it is ubuntu 9.10

---

### Post by neeraj2608 on 2010-01-25
> **repsakkgn said:**
> i just do right click on flash drive icon on the desktop then choose format and then filesystem fat32...tried ntfs - same result.
Have you tried using the "Gnome Format" utility meant for formatting external hard drives? I've used it many a time to format USB drives. Install it with the command:
```

sudo apt-get install gnome-format

```

---

### Post by repsakkgn on 2010-01-25
thanx, gnome-format works well. 
i also tried echo "mtools_skip_check=1" >> ~/.mtoolsrc
but that didn't work.
so the original formatting tool isn't working?

---

