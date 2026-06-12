---
title: "External USB HD doesn't give back free space!"
date: 2010-12-01
forum: Hardware
---

### Post by Jaraqui on 2010-12-01
Nice people from this forum,

   I have an external USB hard disk and, from some time ago until
now, its presenting the following problem.
   I erase several gigabytes from it, but clicking over the properties
option from the HD, the available space doesn't appear. 
   If I try to copy some directory to it, ubuntu says me that there 
isn't enough space (but there is!).
   I did a manual erase from recycle and System Volume Information
directories, but the problem still there.
  
   Does somebody know what's happening?

Regards
Jaraqui
propriertes

---

### Post by gordintoronto on 2010-12-01
Have you run Accessories/Disk Usage Analyzer?

What do you mean by "manual erase from recycle"?

---

### Post by coffeecat on 2010-12-01
> **Jaraqui said:**
> I did a manual erase from recycle and System Volume Information

Do you mean the $RECYCLE.BIN and 'System Volume Information' folders? It's not a good idea to touch those at all. They are part of the (Microsoft) filesystem. I believe the $RECYCLE.BIN folder is only used by Windows.

My guess is that you've deleted some files while using the drive in Ubuntu and not emptied the trash. When you delete something from Ubuntu, the files will go into a hidden folder called .Trash-1000. (Or .Trash-1001, or whatever your user ID is.) They are not physically deleted until you empty the trash. If this is the case, plug the drive in, let it be mounted and empty the trash by clicking on the trash icon on your lower panel at the right.

---

### Post by Jaraqui on 2010-12-01
> **coffeecat said:**
> Do you mean the $RECYCLE.BIN and 'System Volume Information' folders? It's not a good idea to touch those at all. They are part of the (Microsoft) filesystem. I believe the $RECYCLE.BIN folder is only used by Windows.

My guess is that you've deleted some files while using the drive in Ubuntu and not emptied the trash. When you delete something from Ubuntu, the files will go into a hidden folder called .Trash-1000. (Or .Trash-1001, or whatever your user ID is.) They are not physically deleted until you empty the trash. If this is the case, plug the drive in, let it be mounted and empty the trash by clicking on the trash icon on your lower panel at the right.

Thanks people!

   It was that .Trash* something. I really don't know why this folder isn't cleaned
when I click over 'Clean Trash Can".

   What I did was a 'sudo rm -R .Trash*" in a terminal screen.
   The available space returned the real values.

Regards
Jaraqui

---

### Post by coffeecat on 2010-12-01
> **Jaraqui said:**
> What I did was a 'sudo rm -R .Trash*" in a terminal screen.

Why are you using sudo for deleting files/folders on a Microsoft filesystem? With an automounted FAT32 or NTFS drive using sudo is unnecessary.

---

### Post by sgosnell on 2010-12-01
The easy way to do that is to open Nautilus, right-click on the Trash icon, and select Empty Trash.

---

