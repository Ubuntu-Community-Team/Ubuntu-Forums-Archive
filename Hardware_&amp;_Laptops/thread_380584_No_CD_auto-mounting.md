---
title: "No CD auto-mounting"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by K-a-M-u-Z-u on 2007-03-09
hi.
i'm using ubuntu edgy on a IBM ThinkPad R40 laptop.
recently my CD-ROM stoped AUTO-Mount when i insert a cd into the CDROM.
i have to do manual mount each time
my FSTAB:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
/dev/hda5 /   ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
/dev/hda1 /media/hda1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda4
/dev/hda4 /media/hda4     ext3     defaults,   0   1
# /dev/hda3
UUID=b17a9dfd-1bd2-4c4f-8ba2-3a75a0901910 none            swap    sw              0       0
/dev/hdc  /media/cdrom0  udf, iso8859-8,user,noauto  0  0 
```
and the info from "REMOVBLE DRIVES AND MEDIA" menu under SYSTEM-PREFERENCES:
[img]http://grm.m.walla.co.il/briefcase/00f3/k/a/m/u/z/u/@/@/@/@/@/@/@/@/@/@/@/@/@/@/@/@/@/@/@/r/200703100304443121/200703100304587950/snapshot3.jpg[/img]

any idea?
thnx

---

### Post by K-a-M-u-Z-u on 2007-03-10
up?
i counsolted few other sites and no one has replied... :(

---

### Post by larini on 2007-03-11
try this:

1. in removable drivers, uncheck "mount removable media when inserted"
2. insert a cd
3. remove cd
4. check that flag again
5. insert a cd

now it will auto mount..

---

### Post by K-a-M-u-Z-u on 2007-03-11
thanks for the reply, but it didnt help... :( 
is there any other ideas?

---

### Post by K-a-M-u-Z-u on 2007-03-12
another thing,
i cant even open the Cd tray with the button. i need to excute the sudo eject command.
anyone? is this such a difficult problem that no one know a solution for it?

---

