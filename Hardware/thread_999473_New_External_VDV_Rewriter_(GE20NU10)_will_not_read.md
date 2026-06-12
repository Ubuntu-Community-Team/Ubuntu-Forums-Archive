---
title: "New External VDV Rewriter (GE20NU10) will not read cds"
date: 2008-12-01
forum: Hardware
---

### Post by jamescbjr on 2008-12-01
Can read and write DVD's, but when I try to mount a CD I get this message-Unadle to mount location-no media in drive.

etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cdfc8901-f84e-4ac8-94ad-5ff3cc70d6ca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=06c96824-82eb-43b2-9a91-9373bb7cb696 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Can somebody point me in the right direction to get this dvd rom working PLEASE! Thanks

---

### Post by jamescbjr on 2008-12-02
Bump

---

### Post by jamescbjr on 2008-12-03
No help on this FORUM, Going back to Mr Gates):P

---

