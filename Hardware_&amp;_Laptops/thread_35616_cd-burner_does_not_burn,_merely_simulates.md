---
title: "cd-burner does not burn, merely simulates"
date: 2005-05-19
forum: Hardware &amp; Laptops
---

### Post by mattis on 2005-05-19
Hi, there is a problem with my cd-burner, which I need some help with: It is detected and works fine as a cd and dvd reading device. When burning cds ist appears to work normal, but in fact it just simulates (the cds remain blank). When mounting the device manually, I found the following feedback which might be part of the problem:
root@ubuntu:/home/matthias # mount /dev/hdc /media/cdrom0/
mount: blockorientiertes Gerät /dev/hdc ist schreibgeschützt, wird eingehängt im Nur-Lese-Modus
(write protected, mounted read-only)
and this despite the fact that I changed the writing rights of dev/hdc . My fstab-file looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /home ext3 defaults 0 2
/dev/hda1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
any suggestions??
thanks in advance
Matthias

---

### Post by jasmuz on 2005-05-19
[QUOTE=mattis]Hi, there is a problem with my cd-burner, which I need some help with: It is detected and works fine as a cd and dvd reading device. When burning cds ist appears to work normal, but in fact it just simulates (the cds remain blank). When mounting the device manually, I found the following feedback which might be part of the problem:
root@ubuntu:/home/matthias # mount /dev/hdc /media/cdrom0/
mount: blockorientiertes Gerät /dev/hdc ist schreibgeschützt, wird eingehängt im Nur-Lese-Modus
(write protected, mounted read-only)
and this despite the fact that I changed the writing rights of dev/hdc . My fstab-file looks like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /home ext3 defaults 0 2
/dev/hda1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
any suggestions??
thanks in advance
Matthias[/QUOTE]
 What CD recording program have you been using?

---

