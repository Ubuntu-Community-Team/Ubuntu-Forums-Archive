---
title: "fstab - Understanding my partition layout"
date: 2008-07-31
forum: General Help
---

### Post by MaindotC on 2008-07-31
Sup.  I've been reading up on putting the /home partition on a separate partition and I didn't even know I did it but according to my attached picture I did.  I also have the following out put of /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=be428c50-8529-430a-8c1a-9b71eda676b0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=67021796-69cd-438e-b6e2-af4c13872435 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I was reading [this blog post]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") about the directives in fstab.

First question - if I were to re-install, I can install on the 18GB partition, which will create a /home directory of its own, and then when all is said and done I can modify fstab on the new installation with the following line:
```

# /dev/sda3
UUID=67021796-69cd-438e-b6e2-af4c13872435 /home           ext3    relatime        0       2

```
to have the new installation use the existing /home folder that is sitting on the /dev/sda3 (or whatever identifier it assigns) partition?

Second question - the / directory on the 18gb partition grows as I install more apps, correct?  As in - I can't just shrink the partition for the o/s down to like 10GB and expect it to never increase, correct?

Thanks!

---

### Post by MaindotC on 2008-07-31
Sorry - forgot the picture of my part layout - here ya go.

---

### Post by Tim Sharitt on 2008-07-31
On you first question; If you reinstall your current os, it shouldn't be any problem to change /home to the partition you've created. However, a distribution upgrade may cause problems with configuration files, although it may work just fine.
As for your second question, I'm not really sure what your asking but whatever size it is, is what size it will stay until you change it.

---

### Post by MaindotC on 2008-07-31
Thanks, Tim.  I usually don't do dist upgrades - nothing against the people that put in countless hours to write the scripts for them but I usually have less then desirable results (which may be me not upgrade).  On the 2nd question, I just wondered if the operating system (everything but the /home folder) will always stay the same size even if I keep installing .debs or if only the /home folder keeps enlarging.

I'm pretty sure the operating system grows because when I install programs and I see the terminal output I see files being placed in their respective directories, but I just wanted to ask the experts.

---

