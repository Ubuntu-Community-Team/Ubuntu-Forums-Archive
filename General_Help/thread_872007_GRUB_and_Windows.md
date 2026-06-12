---
title: "GRUB and Windows"
date: 2008-07-27
forum: General Help
---

### Post by fox-out on 2008-07-27
does anybody knows how to disable grub and have windows' loader working?
I have two physical harddrives, for windows and xubuntu respectively. loader - grub.
now it is necessary to remove xubuntu harddrive because of physical problems with disk.
when I disconnect xubuntu HD where is a GRUB error 25 at stage 1.5

so how can I get a normal working harddrive with windows?
re-config grub?

---

### Post by argail1980 on 2008-07-27
no, you have to do that from a windows environment, i.e. a rescue console from a windows boot cd. there in the console run

```
fdisk /mbr
```

note that this will remove grub from the boot sector of your disk and write a new master boot record. When you get your ubuntu disk back, you'll have to reinstall grub.

---

### Post by Dr. C on 2008-07-27
You actually need DOS or a DOS like Windows shell. The simplest is to download the Live CD version fullcd.iso of FreeDOS [http://www.freedos.org/]("http://www.freedos.org/") 

Boot into FreeDOS from the Live CD and run the ```
fdisk /mbr
``` command. Alternatively if the computer has a floppy drive one can boot from a DOS floppy disk (MS-DOS, DR-DOS etc) that has the fdisk program and run the command above.

---

### Post by mikewhatever on 2008-07-27
I think the easiest way is to use SuperGrub live cd.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

