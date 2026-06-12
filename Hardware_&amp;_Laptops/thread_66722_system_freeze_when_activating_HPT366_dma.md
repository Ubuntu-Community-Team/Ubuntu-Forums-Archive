---
title: "system freeze when activating HPT366 dma"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by DjMix on 2005-09-18
I have a HPT366 pci ide controller:

0000:00:09.0 Unknown mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372 (rev 01)
0000:00:09.1 Unknown mass storage controller: Triones Technologies, Inc. HPT366/368/370/370A/372 (rev 01)

There are only cdrom attached to it. By default dma is off. I've found a reproducible freeze of the system. If I enable dma in one drive (same thing happen if I use the other, or both) with:
hdparm -d1 /dev/hdf

and then I try to access the cdrom, like
mount /media/cdrom0 (that is /dev/hdf)

the system immediatly freeze. No errors, no warnings. I've tried on a console (CTRL-ALT-F1) with X stopped. Is it a bug on the hpt366 module?


Excuse for my english please!  ;-)

---

### Post by DjMix on 2005-09-19
Nobody else is experiencing the same trouble?

---

