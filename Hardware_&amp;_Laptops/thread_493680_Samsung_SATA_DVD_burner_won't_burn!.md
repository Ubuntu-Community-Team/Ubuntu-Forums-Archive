---
title: "Samsung SATA DVD burner won't burn!"
date: 2007-07-06
forum: Hardware &amp; Laptops
---

### Post by wingnux on 2007-07-06
I've just bought a sata dvd burner that works fine under ubuntu for reading discs but I can't burn any cd/dvd with it! I've already tested it with 5 different programs with no success =/ 

Here's my fstab contents:

proc /proc proc defaults 0 0
# Entry for /dev/hda3 :
UUID=0518e629-18fd-4b2c-a02d-1edabbdf7bbb / reiserfs notail 0 1
# Entry for /dev/hda2 :
UUID=e33c0c4d-acad-4242-a459-060548ae6325 /home ext3 defaults 0 2
# Entry for /dev/sda1 :
UUID=C07CDED07CDEBFF8 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda1 :
UUID=d8fb1c3d-378e-4d53-b9cb-6d927502fd3f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
#/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0 (esta linha comentada era a q o fstab usava automaticamente)

K3B error log:

:-[ MODE SELECT failed with SK=5h/ASC=26h/ACQ=00h]: Input/output error

---

### Post by wingnux on 2007-07-06
Anyone?

---

### Post by midijery on 2007-08-01
I don't know if this has any revelance to your problem. I'm having the same problem with a Pioneer DVR-2810 SATA drive and one thing I noticed on booting is that it insist that it's a sda3 drive instead of sda2 and there is a constant scrolling message when I hit Ctrl Alt F1 thru F6. The message keeps scrolling so fast I can't read it.
By the way I can't remember how to bring  up my fstab entry's in the terminal.

---

