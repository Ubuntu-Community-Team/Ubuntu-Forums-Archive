---
title: "/sbin/init: 432: cannot open dev/console: No such file"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by Arcesso on 2009-01-26
I am in the process of installing the 2.6.28.2 kernel into my Debian machine. 
I currently have 2.6.18-6-686 which works like a charm except for the wireless.  : (
Every time I try to boot into the new kernel it gives me:

initrd-tools: 0.1.84.2
mount: unknown filesystem type 'devfs'
SCSI subsystem initialized
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
umount: devfs: not mounted
mount: unknown filesystem type 'devfs'  		
umount: devfs: not mounted  		
pivot_root: No such file or directory
/sbin/init: 432: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

I understand that devfs is depreciated and so it should not be found anyway,
however it comes up with that error several times.  Also, in the 2.6.18 kernel
dev/console exists.

So far I have tried using

$mount -o loop /boot/initrd.img-2.6.28.2 /intird

 I also tried running

$MAKEDEV update
$MAKEDEV console

using the 2.6.18 kernel to make sure that the directory gets repopulated, however,
 that doesn't seem to work either.

Im on a toshiba satellite laptop

---

### Post by Arcesso on 2009-01-28
bump

---

