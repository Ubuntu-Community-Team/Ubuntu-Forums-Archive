---
title: "cant'e execute files in ntfs"
date: 2008-09-25
forum: General Help
---

### Post by alejaaandro on 2008-09-25
i don't seem to be able to execute files that are in an ntfs hard disk..
i remember i could do that before hardy, but i rarely need to do it, that's why i was a little late to realize it...

i'm trying to run an a.out file that is the output of compiling a fortran program with f77.. if i move it to my desktop it runs ok..

i guess it has something to do with fstab, so here's my configuration for mounting that hard disk

# /dev/sda4
UUID=D8CCC571CCC54B08 /media/Alex_ekswterikos	ntfs	defaults,user,gid=users,uid="username",umask=007 0	1

any ideas? it's not really urgent, but it would make my life easier..


thnx in advance

---

### Post by alejaaandro on 2008-09-28
anybody?

---

### Post by mrog on 2008-09-28
Not sure if this will help, but you could try installing libntfs-gnomevfs.

---

