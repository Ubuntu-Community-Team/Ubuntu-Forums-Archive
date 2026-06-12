---
title: "Grub+WinXP"
date: 2005-12-05
forum: General Help
---

### Post by Ocxic on 2005-12-05
My brother has installed a freash copy of windows xp to his hard drive hdc1 and i would now like to add this installation to my GRUB boot menu so as to allow him to boot XP. i have no idea how to do this. my ubuntu is on hda with GRUB on the MBR. i disabled my drive from the bios so as windows wouldn't overwrite my Grub  bootloader.
so i have:
hda-ubuntu
hdb-storage
hdc-winxp
 what do i do????

---

### Post by humphrey on 2005-12-05
Try adding something like this to the end of /boot/grub/menu.lst

Make sure you back up the original file first :-)

```

# Windows Partition
title           Windows XP
root            (hd2,0)
savedefault
makeactive
chainloader     +1

```

---

