---
title: "writing to ntfs"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by arunsub on 2005-05-27
I have dual boot system (Win XP and Ubuntu). I have C and D drive for Win XP and both are NTFS. I want to make D drive read/write, so I entered the following command in /etc/fstab.  /dev/hda7       /media/ddrive   ntfs    umask=000       0       0. It mounts the NTFS drive, but I'm not able to write to it even though i have given umask=000. I understand that it's security risk etc, but I want to write to NTFS volume. Can somebody help?

---

### Post by rpgcyco on 2005-05-27
You can **not** write to NTFS, it will corrupt it beyond repair, unless you overwrite a file with another file that is exactly the same size. There is another method called CaptiveNTFS (Google for it), but I have no idea if that can be made to work with Ubuntu.

- Rpg Cyco

---

### Post by statix on 2005-05-27
The ntfs modules in the kernel is unable to write to ntfs partitions.  Well actually it can but its extremely limited and pretty much useless.  Look into captive-ntfs.  It uses the native ntfs driver from windows with alittle wine magic to allow writing to an ntfs file system.  It works well but it is quite slow.

---

### Post by jzietman on 2005-05-28
format D: with fat32.  both OSes can read and write to it, and it will be a good inter-OS storage area (which is what you seem to be trying to do with D:, anyway)

---

### Post by bored2k on 2005-05-28
[QUOTE=jzietman]format D: with fat32.  both OSes can read and write to it, and it will be a good inter-OS storage area (which is what you seem to be trying to do with D:, anyway)[/QUOTE]
 Why format when you can convert, keeping old data ?

---

### Post by clb137 on 2005-05-28
[QUOTE=bored2k]Why format when you can convert, keeping old data ?[/QUOTE]


Not too sure you can convert from NTFS to FAT32,,     You can go from FAT32 to NTFS no problem


clint

---

### Post by jzietman on 2005-05-28
copy data from d: to c: temporarily. reformat d: in fat32, then copy music back to c:

i know it's a roundabout method, but a fresh file system is much better than a converted one

---

### Post by arunsub on 2005-05-28
I think i have to format and convert to FAT32. There's no direct and safe method to convert from NTFS to FAT32 though there are some tools avaialable. I don't want to try captive-ntfs since you guys said it's slow and risky. Thanks for the replies.

---

