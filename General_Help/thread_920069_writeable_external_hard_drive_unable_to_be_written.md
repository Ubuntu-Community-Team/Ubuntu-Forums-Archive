---
title: "writeable external hard drive unable to be written to"
date: 2008-09-14
forum: General Help
---

### Post by HangukMiguk on 2008-09-14
I had an (orignally) 80GB vfat external USB HD that was writing as normally, but suddenly ceased writing.  I ran fsck, which told me that I had mismatched tables.  I decided to copy everything needed over to my computer, and reformat the hard drive, to see if that does anything.

I have since reformatted it to both ext3 and reiserfs, and neither will be written to, even though the reformats worked fine, and mounting works fine.

Here is my fstab as of right now:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=29497596-f6a1-40d8-a6c4-49986ad43291 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=0a5cf21a-8354-4e62-b982-7b2e55f1397f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1	/media/SEA_DISC ext3	user,rw,noauto	0	0
```

fsck's of both the reiser and now the ext3 fs's show no abnormalities.

WTF is wrong?

---

### Post by HangukMiguk on 2008-09-14
bump

---

### Post by aloshbennett on 2008-09-15
ls -ld /media/SEA_DISC ?

---

### Post by HangukMiguk on 2008-09-15
```
drwxr-xr-x 3 root root 4096 2008-09-14 21:10 /media/SEA_DISC
```

---

### Post by aloshbennett on 2008-09-15
The folder is owned by root and only root has write permissions. You could give others write access by > sudo chmod a+w /media/SEA_DISC

---

### Post by HangukMiguk on 2008-09-15
> **aloshbennett said:**
> The folder is owned by root and only root has write permissions. You could give others write access by

there was the answer i needed.  thanks!

---

