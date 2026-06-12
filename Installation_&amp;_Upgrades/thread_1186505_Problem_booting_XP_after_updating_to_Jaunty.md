---
title: "Problem booting XP after updating to Jaunty"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Pi72 on 2009-06-13
Hello people.

First of all let me assure you that I've tried many possible solutions and suggestions from these forums and other places trying to fix this problem, but after almost 2 hours of continuous reboots without luck, I'm asking for help.

I had 8.10 and XP living happily together and booting well, although I hardly use XP. I've not booted it since I updated to Jaunty; today I needed to boot into XP and grub gave me "error 13: bad executable format".

I've update-grub'ed, I've fixmbr'ed the windows partition, double checked that the hard drive referred in menu.lst was the right one... But nothing, I can't boot to XP. The related menu.lst entry is this one:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
rootnoverify	(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

This is the output of fdisk -l:

```
root@pi-desktop:~# fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000a872a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2612       38913   291595815   83  Linux
/dev/sda2               1        2611    20972826    5  Extendida
/dev/sda5               1        2497    20057089+  83  Linux
/dev/sda6            2498        2611      915673+  82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

Disco /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 cabezas, 63 sectores/pista, 121601 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x000400da

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1      121601   976760001   83  Linux
/dev/sdb4   *           1           1           0    0  Vacía
La partición 4 no termina en un límite de cilindro.

Disco /dev/sdc: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x633643d7

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       30401   244196001   83  Linux

Disco /dev/sdd: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x020001ff

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdd1   *           1        9728    78140128+   7  HPFS/NTFS

```

Ubuntu is in the first disk, boots ok. Second and third disk don't contain any OS. XP it's in the fourth disk, sdd/hd3, in the first partition (hd0,3 right?)

Things I've done:
update-grub
fixmbr from the XP recovery console
Several combinations of map lines (with/without, using hd0,0 after the mapping...)

Anything I do still gives me error 13. Any ideas?

---

### Post by merlinus on 2009-06-13
Try supergrub to at least boot into xp.  The entries you provided look correct, but perhaps grub did not install to the correct place.

A few other folks solved this kind of problem by creating a small /boot partition at the beginning of their first hdd.

But if you correctly did fixmbr and xp still won't boot directly without going through grub, then something may be corrupted.

---

### Post by Bucky Ball on 2009-06-13
Try it around the other way:

map		(hd3) (hd0)
map		(hd0) (hd3)

---

### Post by Pi72 on 2009-06-15
Well, let's see what I did. First I thought that since nothing worked, maybe XP was really corrupt and I reinstalled it. It still didn't boot from grub. Then I installed grub 2, which messed up things and nothing booted. Managed to recover a working menu.lst, and when reinstalled the normal grub, it messed up things again. I tried a few things and no way. In the end I managed to find an easy way to boot into XP whenever I wanted, but it doesn't use grub. Grub has failed in my setup, I think I know why, but I am already tired of the whole thing to really check that grub can't boot XP if it is in a slave drive.

Thanks to everyone anyway.

---

