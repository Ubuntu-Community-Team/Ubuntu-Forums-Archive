---
title: "MMC not freeing up space after deleting files"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by duan on 2005-08-31
Hi, I find that when I delete files from my MMC card (which mounts fine and pops an icon on the desktop when I plug it in) it doesn't actaully free up space.
I can copy files to it and delete files fine so no acces problems. the lack of space persits through reboots...

gparted gives me: it's msdos, fat 16 format, iUSB Secure Digital  and mounted at /dev/sda/ but i can find it linked to /media/SANVOL/

Any ideas? 
How can I format an MMC/SD card?

Thanks.

---

### Post by Gehaktbal on 2005-08-31
it is because the files are not deleted but moved to the hidden trash folder. Show hidden folders and u will find your files in that folder. Remove them again and then the space will be freed.

---

### Post by duan on 2005-08-31
Thanks!

It's good and clean now.

-Duan

---

