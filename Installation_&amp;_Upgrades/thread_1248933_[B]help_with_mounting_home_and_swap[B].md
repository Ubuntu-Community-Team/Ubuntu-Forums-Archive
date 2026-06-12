---
title: "[B]help with mounting /home and swap[/B]"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by magichsjx on 2009-08-24
[SIZE="3"]hello
ihave installed ubuntu using wubi as opposed to the disk. It did not ler me specify separate home folder and swap. I have 2 partitions one for each and here is my fsatb:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro$
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0     $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


can you help me mount my original /home and swap partitions instead of the default one the wubi installed?[/SIZE]

---

### Post by mikewhatever on 2009-08-24
Is there a problem with accessing these partitions?

---

