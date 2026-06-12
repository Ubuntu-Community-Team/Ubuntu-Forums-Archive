---
title: "strange mount behavior"
date: 2008-11-15
forum: General Help
---

### Post by rkilgore on 2008-11-15
I am trying to mount my new WOW Wrath of the Lich King cdrom and no matter what
I do, it gets mounted with uid=503 and gid=20.  I've tried with and without
options that are supposed to control uid and gid.  Here is the command I would
really like to use:

    sudo mount -t udf -o ro,unhide,uid=1000,gid=1000 /dev/scd0 /media/cdrom0

and here is the output from ls -l /media/cdrom0

    total 8058172
    drwx------ 2 503 dialout        492 Aug 28 22:28 DirectX
    -rwx------ 1 503 dialout 1627861562 Aug 28 22:22 Installer Tome 2.mpq
    -rwx------ 1 503 dialout 2488952542 Aug 28 22:24 Installer Tome 3.mpq
    -rwx------ 1 503 dialout 2375920098 Aug 28 22:26 Installer Tome 4.mpq
    -rwx------ 1 503 dialout 1197605083 Aug 28 22:27 Installer Tome 5.mpq
    -rwx------ 1 503 dialout  124584980 Aug 28 22:27 Installer Tome.mpq
    -rwx------ 1 503 dialout    1407832 Aug 28 22:28 Installer.exe
    -rwx------ 1 503 dialout  435111965 Aug 28 22:28 Movies.mpq
    -rw-r--r-- 1 503 dialout         48 Aug 28 22:28 autorun.inf
    -rw-r--r-- 1 503 dialout     109638 Aug 28 22:28 disc.ico

I don't have a 503 user in /etc/passwd, and adding one makes no difference.
This is the weirdest damn thing.  Has anyone seen anything like this before?

---

### Post by dcstar on 2008-11-15
> **rkilgore said:**
> I am trying to mount my new WOW Wrath of the Lich King cdrom and no matter what
I do, it gets mounted with uid=503 and gid=20.  I've tried with and without
options that are supposed to control uid and gid.  Here is the command I would
really like to use:

    sudo mount -t udf -o ro,unhide,uid=1000,gid=1000 /dev/scd0 /media/cdrom0

.........

I suppose the obvious question is why you aren't using the standard mount stanza that should be in /etc/fstab?

---

