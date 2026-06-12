---
title: "[SOLVED] my cd-roms disappeared"
date: 2008-08-30
forum: General Help
---

### Post by benner on 2008-08-30
i installed a new motherboard. it is a different brand than the last one. i didn't reinstall the OS (ubuntu-Hardy-64) and everything seemed to work so i never gave it a second thought. it has been a couple of weeks and i guess this is the first time i bothered to use the dvd burners. there are 2 and both appear in 'my computer' (when i right click, the location is 'unknown') but neither can mount when i put a disk in.

i thought that ubuntu found everything at boot time so it was no big deal to swap out hardware.  

here's fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d839635c-aa32-4833-8e9a-dad5e281af11 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3d33b7d2-cd15-4a3a-a2ae-19d7469b23ef /home           ext3    relatime        0       2
# /dev/sda3
UUID=c34d4c39-9b15-4401-9f53-6f29f1be8c02 none            swap    sw              0       0
# /dev/sdb3
UUID=4282692c-40bf-4be4-a30d-c8b2a2572798 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

none /proc/bus/usb usbfs devgid=1000,devmode=664 0 0

---

### Post by benner on 2008-08-30
nevermind. looks like it's a hardware problem.

---

### Post by Bliepo32 on 2008-08-30
> **benner said:**
> nevermind. looks like it's a hardware problem.

If you are certain it is a hardware problem, the please mark the thread as solved. That way, people who cannot help you anyway, will not look at your thread, and can spend more time on the threads which do need to be looked at.

Anyway, maybe a cleaning cd might help fix the problem. Or maybe a wire broke off (happened more than once to me).

---

### Post by benner on 2008-08-30
thanks.  maybe dirty. weird, because it happened to both. maybe they got knocked around when i had the new mobo put in. i tried about 20 disks and finally one worked so it isn't a software problem. i keep burning blanks too.

---

