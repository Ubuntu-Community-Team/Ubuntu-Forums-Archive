---
title: "[Hardy] Show new mounted disks on Desktop but not internal mounted disks"
date: 2008-07-12
forum: General Help
---

### Post by mock on 2008-07-12
Hi!
I have a laptop with some ntfs windowspartition mounted on it.
I would like these partions to stay hidden, but i want an icon on the desktop if i insert a cd in my dvd-drive (or plug in a usb-disc).

I know i can disable  apps/nautilus/desktop/ volumes_visible in gconf,
but then i have no icons what so ever.

i have started to "automount" in fstab but still i get the mounted icons on the fixed discs.

in my fstab:

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/Data ntfs-3g defaults,locale=sv_SE.UTF-8 0 0

(now i dont want the /dev/sb1 to appear on the desktop)
(using Hardy gnome)

---

### Post by brendanpiater on 2008-09-26
Same issue here. Know how to switch off all icons for mounted volumes but would still like CD/DVD/USB mounts to show up... any thoughts?

---

