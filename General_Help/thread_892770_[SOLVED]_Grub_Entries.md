---
title: "[SOLVED] Grub Entries"
date: 2008-08-17
forum: General Help
---

### Post by tad1073 on 2008-08-17
I installed the latest greatest kernel (2.6.26-2) throught kerelcheck but kept the same /boot/grub/menu.lst. What do I need to do to add the new kernel?

---

### Post by Jose Catre-Vandis on 2008-08-17
Using nautilus, browse to your /boot directory and identify the latest vmlinuz and initrd files (with 2.6.26-2)

backup menu.lst

```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

open up menu.lst for editing
```
sudo nano /boot/grub/menu.lst
```

scroll down to near the end of file where you should find your current default boot lines, edit as necessary replacing the file names for vmlinuz and initrd as required, or by copying the existing and creating a new entry. Save and reboot.

If you don't get it quite right you can edit the entries from grub. At the grub menu, arrow down or something to stop the booting, then select the line you want to edit and press e. select line you want again and press e to edit. press return when done and b to boot. You always have recovery mode if you can't get booted up.

---

