---
title: "Problem with USB thumbdrive"
date: 2005-04-01
forum: Hardware &amp; Laptops
---

### Post by dude2425 on 2005-04-01
I have this 128MB Lexmark USB thumbdrive, and for some odd reason I cant have a file with a name more than 8 characters long. It worked just fine in Warty, and Fedora Core 3, but when using Hoary it renames everything so that it's less only 8 characters, or if the file had an extension it would be renamed to 8 characters plus three characters of the extension like this:
source~1.lis

Anybody know how to fix this problem while not removing the ability to use it on windows?

---

### Post by cohort on 2005-04-01
IIRC, if it's mounted to the same point every time, you can add an entry to /etc/fstab using the filetype 'vfat' in the third column.

```
/dev/sdb1 /media/thumbdrive vfat rw,user,noauto,sync 0 0
```

(obviously, change the first and second bit to suit *your* system)

---

### Post by dude2425 on 2005-04-01
[QUOTE=cohort]IIRC, if it's mounted to the same point every time, you can add an entry to /etc/fstab using the filetype 'vfat' in the third column.

```
/dev/sdb1 /media/thumbdrive vfat rw,user,noauto,sync 0 0
```

(obviously, change the first and second bit to suit *your* system)[/QUOTE]

Sweet, that worked perfect. Thnx so much!

---

