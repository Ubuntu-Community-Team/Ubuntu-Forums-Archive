---
title: "What should be in /var/archive ?"
date: 2005-11-16
forum: General Help
---

### Post by RyanGT on 2005-11-16
I have over 8 gigs being used in /var/archive.  I think this is do to a recent install of some backup scripts that I didn't fully understand.  The contents is
root@ubuntu:/var/archives# ls -al
total 8269688
drwxrwx---   2 root root       4096 2005-11-16 07:53 .
drwxr-xr-x  16 root root       4096 2005-11-14 08:07 ..
-rw-r--r--   1 root root        121 2005-11-14 08:28 ubuntu-20051114.md5
-rw-r--r--   1 root root        121 2005-11-15 08:34 ubuntu-20051115.md5
-rw-r--r--   1 root root        121 2005-11-16 08:11 ubuntu-20051116.md5
-rw-rw----   1 root root    4859584 2005-11-14 08:07 ubuntu-etc.20051114.tar.gz
-rw-rw----   1 root root    4859659 2005-11-15 08:13 ubuntu-etc.20051115.tar.gz
-rw-rw----   1 root root    4860238 2005-11-16 07:53 ubuntu-etc.20051116.tar.gz
-rw-rw----   1 root root 2807408129 2005-11-14 08:25 ubuntu-home.20051114.tar.gz
-rw-rw----   1 root root 2807444858 2005-11-15 08:31 ubuntu-home.20051115.tar.gz
-rw-rw----   1 root root 2830391211 2005-11-16 08:09 ubuntu-home.20051116.tar.gz

Is it safe to delete these?  They are obviously taking up a huge ammount of disk space.

Thanks,

Ryan

---

### Post by Kyral on 2005-11-16
Those...are the backups themselves

Delete them if you want, its your choice

---

### Post by RyanGT on 2005-11-16
Thanks, that is what I suspected.  I will get rid of all but the latest.

---

