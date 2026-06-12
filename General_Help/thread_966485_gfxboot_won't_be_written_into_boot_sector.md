---
title: "gfxboot won't be written into boot sector"
date: 2008-11-01
forum: General Help
---

### Post by beatlepilz on 2008-11-01
Hello!
The day before yesterday I installed Intrepid on my computer and changed it to my personal requirements. Now I would like to install gfxboot. I tried to install it with the help of the german wiki article. All was good until step where I should write GRUB into the bootsector. There I got this error message:

```
sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.

```

My partitioning is this:

```
Platte /dev/sda: 160.0 GByte, 160041885696 Byte
255 Köpfe, 63 Sektoren/Spuren, 19457 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xf30fb81b

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       16143   129668616    7  HPFS/NTFS
/dev/sda2           16144       19457    26619705    5  Erweiterte
/dev/sda5           19215       19457     1951897+  82  Linux Swap / Solaris
/dev/sda6           16144       19213    24659712   83  Linux

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

I also tried to install GRUB on sda1/sda2/sda5. It was unsuccessful. After booting with my live CD I repaired GRUB. But I want to know, how I can make gfxboot work.
I also posted this in the german community board but I didn't get any answers.
Thanks for your posts in advance.
beatlepilz

---

### Post by beatlepilz on 2008-11-02
Is there nobody who knows anything about this bug?

---

