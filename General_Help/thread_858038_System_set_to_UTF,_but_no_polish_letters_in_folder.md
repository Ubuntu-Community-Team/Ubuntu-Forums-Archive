---
title: "System set to UTF*, but no polish letters in folder/filenames"
date: 2008-07-13
forum: General Help
---

### Post by jefe on 2008-07-13
Hi, got some strange problem with folder/filenames on my vfat partition.
My system is localised to polish, locales are UTF8
LANG=pl_PL.UTF-8
LC_CTYPE="pl_PL.UTF-8"
LC_NUMERIC="pl_PL.UTF-8"
LC_TIME="pl_PL.UTF-8"
LC_COLLATE="pl_PL.UTF-8"
LC_MONETARY="pl_PL.UTF-8"
LC_MESSAGES="pl_PL.UTF-8"
LC_PAPER="pl_PL.UTF-8"
LC_NAME="pl_PL.UTF-8"
LC_ADDRESS="pl_PL.UTF-8"
LC_TELEPHONE="pl_PL.UTF-8"
LC_MEASUREMENT="pl_PL.UTF-8"
LC_IDENTIFICATION="pl_PL.UTF-8"
LC_ALL=
but instead of polish typical letters I get some strange signs, looks like the encoding would be wrong. 
Trying to add to fstab such line:
/dev/sdb1 /mnt/WD vfat user,auto,utf8,umask=0 0 0 
and similar, but no luck.
Whatsmore, I've tried to use convmv to repair. Started with encoding form iso8859-2:
convmv -f latin2 -t utf-8 -r -i /media/WD\ Passport/
but as a result I get many files, folders with comment:
Skipping, already UTF-8
Have no idea what's going on, any help highly appreciate:)

---

