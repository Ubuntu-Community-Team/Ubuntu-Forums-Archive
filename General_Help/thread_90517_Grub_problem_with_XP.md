---
title: "Grub problem with XP"
date: 2005-11-15
forum: General Help
---

### Post by fcalefato on 2005-11-15
Hello, 

I recently added an IDE DVD-RW to my desktop.
Because the ide cable was too short, when conneting the new hardware, I had to switch my XP hard disk to become primary slave, and the DVD-RW is now the primary master. Thus, Grub correctly loads Ubuntu, but freezes when I try to boot XP.

Here is the menu.lst section related to XP:
[I]title Windows XP
rootnoverify (hd0,0)
chainloader +1
makeactive[/I]

How do I fix it to let Grub boot XP correctly?

Thanx a lot guys.

Fabio

---

### Post by slux on 2005-11-15
Changing (hd0,0) to (hd1,0) should do the trick.

---

### Post by fcalefato on 2005-11-15
[QUOTE=slux]Changing (hd0,0) to (hd1,0) should do the trick.[/QUOTE]

I already tried that way, but didtn work. 
Sorry, I forgot to mention it.
Thanks for your reply.

Fabio

---

### Post by metoo on 2005-11-15
I only have a two-liner in grub for win:

title win
    chainloader (hd1,0)+1

If your xp is on hdb1.
(However, that's after installing grub from a SuSE10 install...(tripple boot))

---

### Post by fcalefato on 2005-11-16
Hi,

PartionMagic under DOS showed my MBR was partially corrupted, in that only the FAT32 partition was visible, but not the NTFS bootable one.
I think that FDISK /MBR + reinstalling grub after booting from floppy should do the trick.
Thanks every1 for your help.

f

---

