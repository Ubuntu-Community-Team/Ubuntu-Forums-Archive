---
title: "[SOLVED] Strange file names on shared drive"
date: 2008-11-29
forum: General Help
---

### Post by geear on 2008-11-29
Hello :)

My brother and I are using 2 computers on a network, both running Ubuntu 8.10. He has an external USB drive formated as NTFS which he's sharing over the network. Frequently when he saves a new file, any file, or copies a file to the USB drive, and I try to view it over the network it has this strange name. Here's a few examples:

TC5NWM~H
TMAF4Q~Z

I can open and edit and save the document, no problem. But it keeps that strange name when viewed from my computer, while maintaining the original normal name when viewed from his computer... any ideas?

Thanks!

---

### Post by markharding557 on 2008-11-29
It could be the ntfs can't handle the file names

---

### Post by DGortze380 on 2008-11-29
> **geear said:**
> Hello :)

My brother and I are using 2 computers on a network, both running Ubuntu 8.10. He has an external USB drive formated as NTFS which he's sharing over the network. Frequently when he saves a new file, any file, or copies a file to the USB drive, and I try to view it over the network it has this strange name. Here's a few examples:

TC5NWM~H
TMAF4Q~Z

I can open and edit and save the document, no problem. But it keeps that strange name when viewed from my computer, while maintaining the original normal name when viewed from his computer... any ideas?

Thanks!

how are the shares set up? samba? sftp?

---

### Post by geear on 2008-11-29
Ahh yes! You're right, thanks. Stupid mistake. OpenOffice didn't complain when he tried to save files with punctuation... but I guess NTFS doesn't like it. We removed those and everything is working fine.

Thanks!

---

