---
title: "Format a floppy disc?"
date: 2008-10-08
forum: General Help
---

### Post by flashuni on 2008-10-08
Hello,
     I need help formatting a floppy disc. My new computer needs to update its bios and I need to make a floppy either in Fat 12, Fat 16, or Fat 32.  I have tried gparted, but it doesn't detect the floppy disc.

Please help,
Flashuni :KS

---

### Post by Gondee on 2008-10-08
Check the repos. I know for sure iv seen a floppy formater in there.

---

### Post by Locutus_of_Borg on 2008-10-08
does fdisk detect it?

if so, use whatever it says /dev/fd0 probably and issue
```
mkfs.vfat -F 32 /dev/fd0
```

---

### Post by jerome1232 on 2008-10-08
mtoolsfm - a graphical user interface for accessing dos formatted floppies
floppyd - Daemon for remote access to floppy drives
fdutils - Linux floppy utilities
ufiformat - disk formatter for USB floppy drives


I'm sure one of those floppy utilities can do it.

---

### Post by Shazaam on 2008-10-08
Gparted for me always shows floppies as unformatted space so I don't rely on it.
First open Synaptic and make sure fdutils and gnome-utils is installed. Then pop in the floppy and run this in terminal...
```
gfloppy
```
After you format it the way you want you will need to mount the floppy either through Removable Media or in terminal...
```
sudo mount /dev/fd0 /media/floppy0
```
After your done adding files to the floppy wait at least one minute so data can be written to it before you unmount the floppy. To unmount the floppy right-click the desktop icon and choose "Unmount volume" or run this in terminal...
```
sudo umount /dev/fd0
```
(umount is NOT a typo).

---

