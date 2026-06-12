---
title: "Byteswapping drives from Grub (Tivo related)"
date: 2005-11-14
forum: General Help
---

### Post by Princess_Tiswas on 2005-11-14
I need to byteswap a (Tivo) drive in order to be able to view / access the relevant partitions.

This would be fairly simple from a boot CD written for the job, but I do not currently have access to a working CD drive.

So far, I have added the following line to /boot/grub/menu.lst

/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 **/dev/hdb=bswap** ro quiet splash

However, checking /proc/ide/hdb/settings shows /dev/hdb/ to have a bswap value of 0 (ie. not swapped).

Do I have the wrong syntax in menu.lst?

---

### Post by Princess_Tiswas on 2005-11-15
Looks as though it was the syntax - should have been **hdb=bswap**

---

### Post by dhutton on 2006-11-27
I'm trying to do exactly the same thing, but the dma is still enabled on the drive in question and I cannot figure out how to switch dma off in Ubuntu.

---

