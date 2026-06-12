---
title: "LACIE HD usb - weird behaviour (at least to me)"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by bitebitter on 2006-09-04
Hi, I have a 30 GB usb external hard disk

here's the output of fdisk -l
------------------------------------------------------------
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496    c  W95 FAT32 (LBA)
------------------------------------------------------------

When I issue a df command I receive this:

Filesystem         blocchi di   1K   Usati Disponib. Uso% Montato su
/dev/sda1             29280176  29275408      4768 100% media/LACIE

which is not, because if I issue a du -sch command I receive:
12G     /media/LACIE/
12G     totale

I should have over 15gb free but
when I try to write to the device I receive a "disk full" warning
even though I have plenty of space available.
Any cue?

TIA, Roberto

---

### Post by pelle.k on 2006-09-04
I might be the good ol' stupid nautilus behaviour of not "seeing" the files in .trash folder, created by another installation, or if you forgot to empty trash you put there, before you unmounted it. So now they're there, but magically invisible to nautilus somehow.
This is a bug. Do "ls /media/LACIE/.trash" to see if this is the case.

---

### Post by bitebitter on 2006-09-04
There's no .trash folder in there

---

