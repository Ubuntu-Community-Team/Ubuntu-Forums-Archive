---
title: "deleting partitions"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by iceman.c3k on 2005-03-11
I have Ubuntu running in 20GB of space in my hard drive. It uses partitions /dev/hda9, 10 & 11. I have Debian using partitions /dev/hda6, 7 & 8. Now when I delete the partitions 6, 7 & 8 through fdisk I see that the other partitions get renumbered i.e., /dev/hda9 becomes /dev/hda6 and so on... Under this circumstance, I doubt whether Ubuntu can boot properly, cos' the root partition will now be actually /dev/hda6 and not /dev/hda9. Am I going wrong somewhere? Is my understanding correct? If I have to delete the partitions and have no ther option, how do I proceed to make sure Ubuntu is not at all affected

---

### Post by marsopia on 2005-03-14
If partitions numbers change, you must edit /boot/grub/menu.lst to tell grub where to boot.

Mariano

---

### Post by Xian on 2005-03-14
[QUOTE=iceman.c3k]I have Ubuntu running in 20GB of space in my hard drive. It uses partitions /dev/hda9, 10 & 11. I have Debian using partitions /dev/hda6, 7 & 8. Now when I delete the partitions 6, 7 & 8 through fdisk I see that the other partitions get renumbered i.e., /dev/hda9 becomes /dev/hda6 and so on... [/QUOTE]
You'll also have to edit your /etc/fstab to reflect the new partition scheme.

Actually, that 'drop-down' partition procedure can be tricky on some systems. I'd recommend that you instead just reformat 6,7, & 8 and then copy or move over your 9, 10, and 11 data. You'll still have to edit your menu.lst and fstab configs but it is a much less risky method. After you get it set-up you can then go back and delete the upper partitions or use them for something else.

---

### Post by trigg on 2005-03-15
[QUOTE=Xian]You'll also have to edit your /etc/fstab to reflect the new partition scheme.

Actually, that 'drop-down' partition procedure can be tricky on some systems. I'd recommend that you instead just reformat 6,7, & 8 and then copy or move over your 9, 10, and 11 data. You'll still have to edit your menu.lst and fstab configs but it is a much less risky method. After you get it set-up you can then go back and delete the upper partitions or use them for something else.[/QUOTE]


As for changing the FSTAB and menu.lst, I recommend using a liveCD after the fact - Ubuntu has both Warty and Hoary versions (I used Knoppix - but that was before I discovered Ubuntu).

---

