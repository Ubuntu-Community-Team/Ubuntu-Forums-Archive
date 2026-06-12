---
title: "Install Problem?"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by jasrog on 2006-02-18
I installed Ubuntu permanently, but I did not have option to select yes Grub to MBR loader so how do I know if windows is completely gone?

---

### Post by knalle on 2006-02-18
use **fdisk** to view your partition table

and you can always run **grub-install** afterwards

---

### Post by jasrog on 2006-02-18
how do i run grub install?

---

### Post by knalle on 2006-02-18
from **terminal**, you know how to start a terminal window? do that and write:

**df**

this will show your partitions mounted, see if your disk is **/dev/dha** or **/dev/sda**, then write **fdisk /dev/hda** and use the menu to print the partition table, **q** will quit.

then type **man grub-install** and follow the instructions on how to install GRUB on your mbr

---

### Post by jasrog on 2006-02-18
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            150815780   1715276 141439512   2% /
tmpfs                   517616         0    517616   0% /dev/shm
tmpfs                   517616     12588    505028   3% /lib/modules/2.6.12-9-386/volatile

this is what appears... what do i do now?

---

### Post by taurus on 2006-02-18
Try this command from the terminal then,

fdisk -l /dev/sda

---

### Post by knalle on 2006-02-18
[QUOTE=jasrog]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            150815780   1715276 141439512   2% /
tmpfs                   517616         0    517616   0% /dev/shm
tmpfs                   517616     12588    505028   3% /lib/modules/2.6.12-9-386/volatile

this is what appears... what do i do now?[/QUOTE]

ok, that means sda as harddrive, to instal grub do:

sudo grub-install /dev/sda

---

