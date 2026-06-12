---
title: "Ubuntu can´t recognize my dvd-writer"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by ed.granada on 2007-03-12
Hi! I´m Ed from granada, Spain. I let you read my Big Prolem.
My Ubuntu edgy eft doesn´t detect my DVD-writer. This occurs on a Compaq Laptop (V4832) running  Ubuntu Edgy Eft, kernel 2.6.17-11-generic.

When I try to mount a disk, says:

mount: special device /dev/hdb does not exist

I´ve been watchin in  /dev and hdb doesn´t exist. When I type

dmesg | less

do not detect anything about hdb, and

dmesg | grep hd

only shows:

root@ed-laptop:~# dmesg | grep hd
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash locale=es_ES acpi=off
[ 33.315796] ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[ 33.607611] hda: TOSHIBA MK8025GAS, ATA DISK drive
[ 34.286658] hda: max request size: 128KiB
[ 34.335836] hda: 156301488 sectors (80026 MB), CHS=65535/16/63, UDMA(100)
[ 34.335946] hda: cache flushes supported
[ 34.335973] hda: hda1 hda2
[ 51.622873] EXT3 FS on hda1, internal journal
root@ed-laptop:~#

Nothing about hdb (my dvd-rw, primary slave)

fstab is curious:

/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

I think some day it worked, but something changed, when?

 dmesg says:

[ 33.315796] ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio


then:

sudo fdisk -l

says

ed@ed-laptop:~$ sudo fdisk -l

Disco /dev/hda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio Comienzo Fin Bloques Id Sistema
/dev/hda1 * 1 9355 75144006 83 Linux
/dev/hda2 9356 9729 3004155 5 Extendida
/dev/hda5 9356 9729 3004123+ 82 Linux swap / Solaris

Nothing. I tried:

sudo lsmod

then I tried

modprobe ide_cd cdrom

but nothing.

Someone says that the inly way to fix this is recompiling my kernel... but with wich modules???

PD: I think is obvius, but...
1.- The problem IS NOT the bios, I can´t change nothing
2.- The drive works well.

Some one can give me some clue? Thanks!

---

### Post by rictus007 on 2007-04-22
Hi...I also have this problem and I don't know how to resolve it...but reading other post i found someone saying that make sure that your CD-Rom is properly detected by your BIOS.  It does not work for me...but you should try.

---

### Post by ed.granada on 2007-04-23
Rictus007... I did not published the solution... My DVD Writer was BROKEN!!! I Just changed it, and it works! We always doubt of Ubuntu... It was the fu**** dvd writer, not software... Check it!!!

Ps: My Bios RECOGNIZED it (indeed it was wrong)

---

