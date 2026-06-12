---
title: "Problem with Triple boot system and Windows 8"
date: 2013-10-21
forum: Hardware
---

### Post by spnoe on 2013-10-21
Perhaps I ought not to mention the dreaded Windows 8 here on this forum but I need help and the forum has never let me down. I need to use Windows 8 for certain programes but for some reason a recent program seems to have broken the Boot. I tried using the Windows 8 disk to repair its own boot but it just hang and then on one occassion a message said File\boot\BCD, Status Ox00000e9, Info an unexpected I/O error. I decide to use GParted to Delete and Re-format theWindows partition but Gparted just hung at SDA. So then I decided to use a System Boot Repair disk which repaired the Ubuntu and XP partitions (XP is on the same disk as Windows 8. On trying Gpated again nothing but I did get this message somehow;

Error mounting /dev/sda1 at /media/stephen/FEA63B85A63B3D89: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/stephen/FEA63B85A63B3D89"' exited with non-zero exit status 18: Failed to write lock '/dev/sda1': Resource temporarily unavailable
Error opening '/dev/sda1': Resource temporarily unavailable
Failed to mount '/dev/sda1': Resource temporarily unavailable

This means nothing to me. Could someone advise me what the proble can be and how I can rectify it.

Help as usual most gratefully received,
Steve

---

### Post by mkmanifesto on 2013-10-21
It sounds like a master boot record problem. I haven't had any experience repairing the MBR for a multiboot system. Hopefully someone will be able to help you.

Also what were you doing prior to this issue coming up? Was everything previously working? It could be many different things causing this problem.

---

